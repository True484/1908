# 1908
from pywebio.input import input
from pywebio.output import put_text, put_success, put_error
from pywebio.session import run_async
import logging

# Налаштування логування
logging.basicConfig(level=logging.DEBUG, format='%(asctime)s - %(levelname)s - %(message)s')
logger = logging.getLogger()

# Запитання для вікторини
questions = [
    {"question": "Яка планета є найбільшою у Сонячній системі?", "answer": "юпітер"},
    {"question": "Скільки континентів на Землі?", "answer": "7"},
    {"question": "Як називається столиця Франції?", "answer": "париж"},
    {"question": "Який метал є основним у виробництві алюмінієвої фольги?", "answer": "алюміній"},
    {"question": "Скільки кольорів у веселці?", "answer": "7"}
]

def school_quiz():
    # Запит імені користувача
    user_name = input("Введіть своє ім'я:")
    logger.info(f"Користувач почав вікторину: {user_name}")
    
    score = 0  # Лічильник правильних відповідей

    for i, item in enumerate(questions, start=1):
        user_answer = input(item['question']).strip().lower()
        correct_answer = item['answer'].lower()

        if user_answer == correct_answer:
            put_success(f"Вірно! {item['question']} → {user_answer}")
            score += 1
        else:
            put_error(f"Невірно! {item['question']} → {user_answer}. Правильна відповідь: {item['answer']}")

        # Логування відповіді
        logger.debug(f"Запитання {i}: {item['question']} → Відповідь: {user_answer}, Правильна: {correct_answer}")

    # Розрахунок результатів
    total_questions = len(questions)
    percentage = (score / total_questions) * 100
    put_text(f"{user_name}, ви набрали {score} із {total_questions} правильних відповідей.")
    put_text(f"Це становить {percentage:.2f}% правильних відповідей.")

    # Логування фінального результату
    logger.info(f"Результат {user_name}: {score}/{total_questions} ({percentage:.2f}%)")

# Запуск додатку
if __name__ == "__main__":
    from pywebio import start_server
    start_server(school_quiz, port=8080)
