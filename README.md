# ECE2112-PA2

**Made by:** Kennette L. Garcia | **Section:** 2ECE-B

The content of this repository is the **Programming Assignment No. 2** for our course **"ECE 2112: Advanced Computer Programming and Algorithms"**. This assignment focuses on NumPy arrays.

---

## Intended Learning Outcomes (Objectives)

1. Create and reshape NumPy arrays using appropriate NumPy functions.
2. Perform vectorized numerical operations on an `ndarray`.
3. Compute array statistics and use Boolean conditions to select elements.
4. Save computed NumPy arrays as `.npy` files.

---

## 1. Reproducible Normalization Problem

Create a reproducible random `5 × 5` integer ndarray named `X` using a specified random seed. The array is then normalized using its overall mean and population standard deviation.

The normalization formula used is:

$$
Z = \frac{X-\bar{x}}{\sigma}
$$

where `x̄` is the mean of all 25 elements and `σ` is the population standard deviation returned by NumPy's `std()` function.

### Explanation:
* **`np.random.seed()`**: Sets the random seed to make the generated array reproducible.
* **`np.random.randint()`**: Generates random integers within the specified range and creates the `5 × 5` array.
* **`np.sum()`**: Calculates the sum of all elements in the array.
* **`X.size`**: Returns the total number of elements in the array.
* **`np.std()`**: Calculates the population standard deviation of the array.
* **Array Arithmetic**: Performs element-wise subtraction and division to normalize every element.
* **`np.mean()`**: Checks the mean of the normalized array.
* **`np.save()`**: Saves the normalized array as a NumPy `.npy` file.

```python
import numpy as np
np.random.seed(2112)

X = np.random.randint(10, 101, size=(5, 5))

sum = float(np.sum(X))

mean = sum / X.size

sd = float(np.std(X))

X_normalized = (X - mean) / sd

np.mean(X_normalized)

np.std(X_normalized)

np.save("X_normalized.npy", X_normalized)
```

The normalized array has a mean approximately equal to `0` and a standard deviation approximately equal to `1`, subject to floating-point rounding.

---

## 2. Cubes Divisible by 4 Problem

Create the first 100 positive integers, cube every element, and reshape the resulting values into a `10 × 10` ndarray named `C`. Boolean filtering is then used to select only the cubed values that are divisible by `4`.

### Explanation:
* **`np.arange()`**: Creates the sequence of positive integers from `1` to `100`.
* **Array Exponentiation (`** 3`)**: Cubes every element of the NumPy array using vectorized arithmetic.
* **`.reshape()`**: Reshapes the resulting one-dimensional array into a `10 × 10` ndarray.
* **Modulo Operator (`%`)**: Determines whether each cubed value is divisible by `4`.
* **Boolean Filtering**: Selects only the elements satisfying the divisibility condition.
* **`.size`**: Counts the number of selected elements.
* **`np.save()`**: Saves the selected values as a NumPy `.npy` file.

```python
numbers = np.arange(1, 101)

C = numbers ** 3

C = C.reshape(10, 10)

div_by_4 = C[C % 4 == 0]

div_by_4.size

np.save("div_by_4.npy", div_by_4)
```

The resulting `C` array has a shape of `(10, 10)`, while `div_by_4` contains `50` selected elements. The first selected value is `8` and the last is `1,000,000`.

---

## 3. Above-Mean Squares Problem

Create a `6 × 6` ndarray named `S` containing the squares of the first 36 positive integers in increasing row-major order. The mean of all elements is then calculated, and Boolean filtering is used to select only the elements strictly greater than the mean.

### Erplanation:
* **`np.arange()`**: Creates the sequence of positive integers from `1` to `36`.
* **Array Exponentiation (`** 2`)**: Squares every element using vectorized arithmetic.
* **`.reshape()`**: Reshapes the squared values into a `6 × 6` ndarray.
* **`np.mean()`**: Calculates the mean of all elements in `S`.
* **Boolean Filtering**: Selects only elements that are strictly greater than `S_mean`.
* **`.size`**: Counts the number of selected elements.
* **`np.save()`**: Saves the selected values as a NumPy `.npy` file.

```python
numbers = np.arange(1, 37)

S = numbers ** 2

S = S.reshape(6, 6)

S_mean = float(np.mean(S))

above_mean = S[S > S_mean]

above_mean.size

np.save("above_mean.npy", above_mean)
```

The resulting `above_mean` array contains `15` selected elements. The first selected value is `484` and the last is `1296`.
