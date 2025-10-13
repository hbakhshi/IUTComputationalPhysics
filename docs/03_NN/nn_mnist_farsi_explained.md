
# 🧠 راهنمای گام‌به‌گام کد شبکه‌ی عصبی (MNIST) در پایتون

## 🔎 ۱. ایده‌ی کلی

- این درس، پیاده‌سازی ساده‌ای از یک **شبکه‌ی عصبی پیش‌خور** (feed‑forward) را با استفاده از دستورات پایه‌ی پایتون و NumPy ارائه می‌دهد.
- هدف اصلی: طبقه‌بندی تصاویر دست‌نویس MNIST، یعنی ۱۰ کلاس رقمی، بدون وابستگی به فریم‌ورک‌های حجیم.
- پیاده‌سازی با الهام از کتاب *Neural Networks and Deep Learning* انجام شده است.

---

## 🧱 ۲. ساختار کلاس `Network`

```python
class Network(object):
    def __init__(self, sizes):
        self.num_layers = len(sizes)
        self.sizes = sizes
        self.biases = [np.random.randn(y, 1) for y in sizes[1:]]
        self.weights = [np.random.randn(y, x) for x, y in zip(sizes[:-1], sizes[1:])]
```

- لیست `sizes` عرض ورودی، تعداد نورون‌های لایه‌های پنهان، و خروجی‌ها را تعیین می‌کند.  
  مثال: `[784, 30, 10]` برای MNIST.
- `biases` و `weights` با نمونه‌گیری از توزیع نرمال مقداردهی اولیه می‌شوند.

### ویژگی `nParams`

```python
@property
def nParams(self):
    return sum(w.size for w in self.weights) + sum(b.size for b in self.biases)
```

---

## 🚀 ۳. پیش‌خور (Feedforward)

```python
def feedforward(self, a, verbose=False):
    for b, w in zip(self.biases, self.weights):
        if verbose:
            print("وزن:", w.shape, "بایاس:", b.shape)
        a = sigmoid(w @ a + b)
    return a
```

---

## 🔄 ۴. انتشار معکوس (Backpropagation)

```python
def backprop(self, x, y):
    activation = x
    activations = [x]
    zs = []
    for b, w in zip(self.biases, self.weights):
        z = w.dot(activation) + b
        zs.append(z)
        activation = sigmoid(z)
        activations.append(activation)

    delta = self.cost_derivative(activations[-1], y) * sigmoid_prime(zs[-1])
    nabla_b[-1] = delta
    nabla_w[-1] = np.dot(delta, activations[-2].T)
    for l in range(2, self.num_layers):
        z = zs[-l]
        sp = sigmoid_prime(z)
        delta = np.dot(self.weights[-l+1].T, delta) * sp
        nabla_b[-l] = delta
        nabla_w[-l] = np.dot(delta, activations[-l-1].T)
    return (nabla_b, nabla_w)
```

---

## 🧪 ۵. آموزش با گرادیان کاهش تصادفی (SGD)

```python
def update_mini_batch(self, mini_batch, eta):
    for x, y in mini_batch:
        delta_b, delta_w = self.backprop(x, y)
        nabla_b = [nb + db for nb, db in zip(nabla_b, delta_b)]
        nabla_w = [nw + dw for nw, dw in zip(nabla_w, delta_w)]
    self.weights = [w - (eta / len(mini_batch)) * nw for w, nw in zip(self.weights, nabla_w)]
    self.biases = [b - (eta / len(mini_batch)) * nb for b, nb in zip(self.biases, nabla_b)]
```

---

## 📦 ۶. توابع سیگموئید و مشتق آن

```python
def sigmoid(z): return 1.0 / (1.0 + np.exp(-z))
def sigmoid_prime(z): return sigmoid(z) * (1 - sigmoid(z))
```

---

## 📂 ۷. بارگذاری و نمایش داده‌ی MNIST

```python
training_data, validation_data, test_data = load_data()
yvalues = np.zeros((50000, 10))
yvalues[np.arange(50000), training_data[1]] = 1
training_d = list(zip(...))
test_d = list(zip(...))
```

---

## 📊 ۸. مثال اجرا و نتایج

```python
nn.SGD(training_d, epochs=5, mini_batch_size=1000, eta=1.0, test_data=test_d)
```

---

## 🔧 ۱۰. نحوه‌ی استفاده در صفحه‌ی وب

```html
<details>
  <summary>توضیحات کامل شبکه</summary>

  <!-- اینجا متن مارک‌داون قرار گیرد -->
</details>
```

---
