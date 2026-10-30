
        time.sleep(3)

        print("Текущий URL:", driver.current_url)
        page_text = driver.find_element(By.TAG_NAME, "body").text
        print("Текст страницы:", page_text)

        # Проверяем, что появилась ожидаемая ошибка
        assert (
            "Неправильное имя пользователя или пароль" in page_text
            or "капч" in page_text.lower()
            or "captcha" in page_text.lower()
        ), "Не найдено сообщение об ошибке логина или капче"

        print("Test passed successfully!")
        driver.quit()



