# 开始
文档地址: <https://playwright.dev/python/docs/intro>

## 安装
pip install playwright==1.25.2 

### 安装 Pytest plugin
pip install pytest-playwright==0.3.0

---

### 安装浏览器
playwright install chromium

---

### 运用测试用例
test_my_application.py

```
import re
from playwright.sync_api import Page, expect

def test_homepage_has_Playwright_in_title_and_get_started_link_linking_to_the_intro_page(page: Page):
    page.goto("https://playwright.dev/")

    # Expect a title "to contain" a substring.
    expect(page).to_have_title(re.compile("Playwright"))

    # create a locator
    get_started = page.locator("text=Get Started")

    # Expect an attribute "to be strictly equal" to the value.
    expect(get_started).to_have_attribute("href", "/docs/intro")

    # Click the get started link.
    get_started.click()

    # Expects the URL to contain intro.
    expect(page).to_have_url(re.compile(".*intro"))
```

---

# todo https://playwright.dev/python/docs/writing-tests


## Pytest Plugin Reference
pytest --browser chromium --headed blue/tests/playwright

## [Fixtures](https://playwright.dev/python/docs/test-runners#fixtures)

```
def test_my_app_is_working(
        context, page, playwright, browser_type, browser, browser_name, browser_channel, is_chromium,
        is_webkit, is_firefox, browser_type_launch_args, browser_context_args):
    with open('a.log', 'wb') as f:
        f.write(f'{context=}\n'.encode('utf8'))
        f.write(f'{page=}\n'.encode('utf8'))
        f.write(f'{playwright=}\n'.encode('utf8'))
        f.write(f'{browser_type=}\n'.encode('utf8'))
        f.write(f'{browser=}\n'.encode('utf8'))
        f.write(f'{browser_name=}\n'.encode('utf8'))
        f.write(f'{browser_channel=}\n'.encode('utf8'))
        f.write(f'{is_chromium=}\n'.encode('utf8'))
        f.write(f'{is_webkit=}\n'.encode('utf8'))
        f.write(f'{is_firefox=}\n'.encode('utf8'))
        f.write(f'{browser_type_launch_args=}\n'.encode('utf8'))
        f.write(f'{browser_context_args=}\n'.encode('utf8'))
```

## 多进程
pytest --browser chromium --numprocesses 8  blue/tests/playwright

# 开始
## 安装 

安装会自动下载浏览器，查看方式：  
- %USERPROFILE%\AppData\Local\ms-playwright on Windows
- ~/Library/Caches/ms-playwright on MacOS
- ~/.cache/ms-playwright on Linux

## 用法
```
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page()
    page.goto("http://playwright.dev")
    print(page.title())
    browser.close()
```

## 打包程序：Pyinstaller

PLAYWRIGHT_BROWSERS_PATH=0 playwright install chromium  
pyinstaller -F main.py  
双击运用 dist 中 的执行文件






## todo https://playwright.dev/python/docs/test-runners#examples