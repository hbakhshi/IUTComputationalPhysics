
# 🧠 راهنمای جامع و خط‌به‌خط کد شبکه‌ی عصبی ساده (MNIST)

این راهنما به بررسی دقیق ساختار و منطق یک شبکه‌ی عصبی ساده که برای طبقه‌بندی تصاویر مجموعه داده‌ی MNIST طراحی شده، می‌پردازد. هر بخش از کد با توضیحات کامل فارسی همراه است.

---

## 🔧 ۱. ساختار کلی کلاس `Network`

```python
class Network(object):
    def __init__(self, sizes):
        self.num_layers = len(sizes)
        self.sizes = sizes
        self.biases = [np.random.randn(y, 1) for y in sizes[1:]]
        self.weights = [np.random.randn(y, x) for x, y in zip(sizes[:-1], sizes[1:])]
```

### 📘 توضیح خط به خط:

- `class Network(object):`  
  تعریف کلاس شبکه‌ی عصبی. این کلاس شامل وزن‌ها، بایاس‌ها و توابع آموزش است.

- `def __init__(self, sizes):`  
  تابع سازنده که آرایه‌ای به نام `sizes` می‌گیرد، شامل تعداد نورون‌ها در هر لایه.

- `self.num_layers = len(sizes)`  
  تعیین تعداد لایه‌ها بر اساس طول آرایه‌ی `sizes`.

- `self.sizes = sizes`  
  ذخیره لیست ساختار لایه‌ها در ویژگی `sizes`.

- `self.biases = [np.random.randn(y, 1) for y in sizes[1:]]`  
  مقداردهی اولیه بایاس‌ها برای تمام لایه‌های غیر از ورودی.  
  بایاس هر نورون از توزیع نرمال استاندارد (`mean=0, std=1`) مقداردهی می‌شود.

- `self.weights = [np.random.randn(y, x) for x, y in zip(sizes[:-1], sizes[1:])]`  
  مقداردهی اولیه وزن‌ها بین هر دو لایه‌ی متوالی.  
  وزن‌ها ماتریس‌هایی با ابعاد `(تعداد نورون‌های لایه‌ی فعلی × تعداد نورون‌های لایه‌ی قبلی)` هستند.

---

## 🧮 ۲. محاسبه تعداد پارامترها

```python
@property
def nParams(self):
    return sum(w.size for w in self.weights) + sum(b.size for b in self.biases)
```

### 📘 توضیح:

- این ویژگی تعداد کل پارامترهای قابل یادگیری (وزن + بایاس) در شبکه را بازمی‌گرداند.

- `w.size` و `b.size` تعداد عناصر هر وزن و بایاس را محاسبه می‌کند.

---

## 🔁 ۳. پیش‌خور (Feedforward)

```python
def feedforward(self, a, verbose=False):
    for b, w in zip(self.biases, self.weights):
        if verbose:
            print("وزن:", w.shape, "بایاس:", b.shape)
        a = sigmoid(w @ a + b)
    return a
```

### 📘 توضیح:

- `a` ورودی اولیه شبکه (تصویر مسطح شده) است.
- در هر لایه:
  - ابتدا `z = w @ a + b` محاسبه می‌شود.
  - سپس سیگموئید روی آن اعمال می‌شود.
  - `a` برای لایه بعدی به‌روز می‌شود.

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

### 📘 توضیح:

- مرحله feedforward را تکرار می‌کند و `z` و `activation`‌ها را ذخیره می‌کند.
- در مرحله برگشتی:
  - گرادیان تابع هزینه محاسبه می‌شود.
  - سپس گرادیان‌ها برای تمام وزن‌ها و بایاس‌ها در هر لایه به‌دست می‌آید.
  - از مشتق تابع سیگموئید استفاده می‌شود.

---

## 🧪 ۵. به‌روزرسانی وزن‌ها با Mini-Batch

```python
def update_mini_batch(self, mini_batch, eta):
    for x, y in mini_batch:
        delta_b, delta_w = self.backprop(x, y)
        nabla_b = [nb + db for nb, db in zip(nabla_b, delta_b)]
        nabla_w = [nw + dw for nw, dw in zip(nabla_w, delta_w)]
    self.weights = [w - (eta / len(mini_batch)) * nw for w, nw in zip(self.weights, nabla_w)]
    self.biases = [b - (eta / len(mini_batch)) * nb for b, nb in zip(self.biases, nabla_b)]
```

### 📘 توضیح:

- برای هر mini-batch از داده‌های آموزشی:
  - گرادیان‌ها محاسبه می‌شود.
  - وزن‌ها و بایاس‌ها با میانگین گرادیان‌ها و نرخ یادگیری `eta` به‌روزرسانی می‌شوند.

---

## 🔢 ۶. توابع سیگموئید و مشتق آن

```python
def sigmoid(z): return 1.0 / (1.0 + np.exp(-z))
def sigmoid_prime(z): return sigmoid(z) * (1 - sigmoid(z))
```

### 📘 توضیح:

- سیگموئید تابع فعال‌سازی استاندارد برای نورون‌هاست.
- مشتق آن برای backpropagation ضروری است.

---

## 📂 ۷. بارگذاری داده‌های MNIST

```python
training_data, validation_data, test_data = load_data()
yvalues = np.zeros((50000, 10))
yvalues[np.arange(50000), training_data[1]] = 1
training_d = list(zip(...))
```

### 📘 توضیح:

- داده‌ها شامل تصاویر و برچسب‌ها است.
- برچسب‌ها به صورت one-hot encoded تبدیل می‌شوند تا برای خروجی softmax آماده باشند.

---

## ▶️ ۸. آموزش مدل

```python
nn.SGD(training_d, epochs=5, mini_batch_size=1000, eta=1.0, test_data=test_d)
```

### 📘 توضیح:

- شبکه با استفاده از الگوریتم SGD آموزش داده می‌شود.
- در هر دوره (epoch) وزن‌ها با استفاده از mini-batchها اصلاح می‌شوند.

---

## 🔧 ۹. استفاده در HTML

```html
<details>
  <summary>توضیحات کامل شبکه</summary>

  <!-- اینجا متن مارک‌داون قرار گیرد -->
</details>
```

---

