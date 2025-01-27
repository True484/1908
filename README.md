def check_and_add(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        if isinstance(result, int):  # Перевірка, чи результат є цілим числом
            return result + 10
        return result  # Якщо не ціле число, просто повертаємо результат
    return wrapper

# Приклад використання
@check_and_add
def my_function(x):
    return x * 2

@check_and_add
def another_function(x):
    return x / 2

print(my_function(5))  # 20 (5*2 + 10)
print(another_function(5))  # 2.5 (не ціле число)
