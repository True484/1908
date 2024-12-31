import requests

# Отримання даних із API
response = requests.get("https://dummyjson.com/users")
data = response.json()['users']

# Підрахунки
younger_than_30 = sum(1 for user in data if user['age'] < 30)
women_with_green_eyes = sum(1 for user in data if user['gender'] == 'female' and user['eyeColor'] == 'green')
living_in_san_francisco = sum(1 for user in data if user['address']['city'] == 'San Francisco')

# Виведення результатів
print(f"Кількість користувачів молодше 30 років: {younger_than_30}")
print(f"Кількість жінок із зеленими очима: {women_with_green_eyes}")
print(f"Кількість людей, які живуть у San Francisco: {living_in_san_francisco}")
