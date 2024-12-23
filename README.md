# rectangle_area.py

def calculate_rectangle_area(length, width):
    """
    Обчислює площу прямокутника.
    :param length: Довжина прямокутника
    :param width: Ширина прямокутника
    :return: Площа прямокутника
    """
    if length <= 0 or width <= 0:
        raise ValueError("Довжина та ширина повинні бути більше нуля")
    return length * width


# test_rectangle_area.py

import pytest
from rectangle_area import calculate_rectangle_area

def test_positive_case():
    assert calculate_rectangle_area(5, 3) == 15

def test_zero_length():
    with pytest.raises(ValueError):
        calculate_rectangle_area(0, 3)

def test_negative_width():
    with pytest.raises(ValueError):
        calculate_rectangle_area(5, -2)


