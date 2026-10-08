# web_form_automation
#code
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait, Select
from selenium.webdriver.support import expected_conditions as EC
import time



driver = webdriver.Chrome()
wait = WebDriverWait(driver, 10)

driver.get("https://www.selenium.dev/selenium/web/web-form.html")


print("TC01 - Open Web Form")

if "web-form" in driver.current_url:
    print("TC01 - Page opened successfully")
else:
    print("TC01 - Page opening failed")

print("\nTC02 - Locate Username")

username = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//*[@id='my-text-id']")
    )
)

username.send_keys("sriram")

print("TC02 - Username entered successfully")


print("\nTC03 - Enter Password")

password = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//input[@type='password']")
    )
)

password.send_keys("Sriram@123")

print("TC03 - Password entered successfully")


print("\nTC04 - Locate Submit Button")

submit = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[text()='Submit']")
    )
)

print("TC04 - Submit button located successfully")


print("\nTC05 - Locate Textbox Dynamically")

dynamic_textbox = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//input[contains(@id,'my-text')]")
    )
)

print("TC05 - Dynamic textbox located successfully")



print("\nTC06 - Locate Element Using starts-with()")

prefix_element = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//input[starts-with(@id,'my-text')]")
    )
)

print("TC06 - Prefix element located successfully")


print("\nTC07 - Find Input Using Two Attributes")

username_two_attributes = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//input[@type='text' and @id='my-text-id']")
    )
)

print("TC07 - Element found using two attributes")



print("\nTC08 - Find Element Using OR")

alternative_element = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//input[@id='my-text-id' or @name='my-text']")
    )
)

print("TC08 - Element found using OR")



print("\nTC09 - Find Parent Element")

parent_element = wait.until(
    EC.presence_of_element_located(
        (By.XPATH, "//input[@id='my-text-id']/parent::*")
    )
)

print("TC09 - Parent element located successfully")



print("\nTC10 - Find All Input Fields")

input_fields = driver.find_elements(
    By.XPATH,
    "//input"
)

print("TC10 - Total input fields:", len(input_fields))

for i, field in enumerate(input_fields, start=1):
    print("Input", i, "->", field.get_attribute("type"))



time.sleep(5)

driver.quit()
```

#output
<img width="817" height="397" alt="image" src="https://github.com/user-attachments/assets/878a3fb7-85dc-4d82-96dd-bfb7ce02dbdb" />
<img width="1236" height="813" alt="image" src="https://github.com/user-attachments/assets/ca4dbb3d-c94b-49d8-a3ee-673e244ec849" />

