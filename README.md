
from selenium import webdriver
from selenium.webdriver.common.by import By
import time  # ДОБАВЛЕНО, если ещё нет в твоём коде


def test_login_form():
    driver = webdriver.Chrome()

    try:
        driver.get("https://b2c.passport.rt.ru")
        time.sleep(2)

        # Открываем вкладку входа
        driver.find_element(By.ID, "t-btn-tab-login").click()

        # Заполняем логин и пароль
        driver.find_element(By.ID, "username").send_keys("test_user")
        driver.find_element(By.ID, "password").send_keys("test_password")

        # Нажимаем кнопку входа
        driver.find_element(By.ID, "kc-login").click()

        # ДОБАВЛЕНО: оставляем браузер открытым для капчи
        input("Реши капчу в браузере, затем нажми Enter в терминале...")

        # Проверяем сообщение об ошибке входа
        error_msg = driver.find_element(
            By.CLASS_NAME, "card-error"
        ).text

        assert "Неправильное имя пользователя или пароль" in error_msg

        print("Test passed successfully")

    finally:
        driver.quit()


test_login_form()
