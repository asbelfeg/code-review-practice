
print("Текущий URL:", driver.current_url)
print(driver.find_element(By.TAG_NAME, "body").text[:3000])
input("Посмотри страницу в браузере и нажми Enter здесь...")

