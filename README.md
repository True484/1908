# 1908
"""
Симулятор каси магазину
Виправлений код для розрахунку чека.
"""

import textwrap
from datetime import datetime
from decimal import Decimal, ROUND_HALF_UP

# Функція для форматування ціни
def format_price(value):
    return Decimal(value).quantize(Decimal('0.01'), rounding=ROUND_HALF_UP)

# Введення даних для першого товару
item_1_title = textwrap.shorten(input('Введіть назву першого товару: ').ljust(20, '.'), width=20, placeholder='...')
item_1_quantity = int(round(float(input('Введіть бажаєму кількість першого товару: '))))
item_1_price = format_price(input('Введіть ціну першого товару: '))

# Введення даних для другого товару
item_2_title = textwrap.shorten(input('Введіть назву другого товару: ').ljust(20, '.'), width=20, placeholder='...')
item_2_quantity = int(round(float(input('Введіть бажаєму кількість другого товару: '))))
item_2_price = format_price(input('Введіть ціну другого товару: '))

# Розрахунок вартості товарів
item_1_total_cost = format_price(item_1_quantity * item_1_price)
item_2_total_cost = format_price(item_2_quantity * item_2_price)

# Загальний результат
total_cost = item_1_total_cost + item_2_total_cost

# Шаблон для друку
printing_template = '{}\t\t\t\t{}\t\t\t{}\t\t\t{}'

# Друк чека
print('\n\n\n')
print('Фіскальний чек'.capitalize().center(80, '~'))
print('МАГАЗИН "ВСЕ ДЛЯ ДОМУ"'.center(80))
print(f'Товар\t\t\t\tКількість\t\tЦіна\t\tВартість')
print(printing_template.format(item_1_title, item_1_quantity, f"{item_1_price:.2f}", f"{item_1_total_cost:.2f}"))
print(printing_template.format(item_2_title, item_2_quantity, f"{item_2_price:.2f}", f"{item_2_total_cost:.2f}"))
print('~' * 80)
print(printing_template.format(
    'ВСЬОГО'.ljust(20),
    '-',
    '-',
    f"{total_cost:.2f}"
))
print(datetime.now().strftime('%d-%m-%Y %H:%M:%S').rjust(80))
print('\n\n')

