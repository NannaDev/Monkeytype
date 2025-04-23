# after open click in "accept all" fast or error in code if it happened just try again
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time
import random

EMAIL = "" # you account gmail
PASSWORD = "" # you account password
TYPING_SPEED = 0.00001

driver = webdriver.Chrome()
wait = WebDriverWait(driver, 15)

def login():
    print("logging in...")
    driver.get("https://monkeytype.com/login")
    time.sleep(2)

    email = wait.until(EC.presence_of_element_located((By.NAME, "current-email")))
    email.send_keys(EMAIL)
    time.sleep(1)

    password = driver.find_element(By.NAME, "current-password")
    password.send_keys(PASSWORD)
    time.sleep(1)

    driver.find_element(By.CSS_SELECTOR, "button.signIn").click()
    time.sleep(3)

def run_test():
    print("starting...")
    driver.get("https://monkeytype.com")
    time.sleep(2)

    input_field = wait.until(EC.presence_of_element_located((By.ID, "wordsInput")))
    print("typing...")

    while True:
        try:
            word = wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, ".word.active")))
            for char in word.text:
                input_field.send_keys(char)
                time.sleep(random.uniform(TYPING_SPEED * 5.5, TYPING_SPEED * 5.5))
            input_field.send_keys(" ")
            time.sleep(0.05)
        except Exception as e:
            print(f"error type: {e}")
            break

def check_xp():
    try:
        xp_element = wait.until(EC.presence_of_element_located((By.XPATH, "//div[contains(text(), '+')]")))
        xp_text = xp_element.text
        print(f"XP: {xp_text}")
        return True
    except:
        print("Fail Get XP.")
        return False

def restart_test():
    print("Restart...")
    driver.get("https://monkeytype.com")
    time.sleep(1.25)

login()

while True:
    run_test()
    time.sleep(2)
    check_xp()
    restart_test()
