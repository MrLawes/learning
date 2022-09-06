# Pytest Plugin Reference
文档地址: <https://playwright.dev/python/docs/intro>

## 安装
pip install pytest-playwright==0.3.0

## 用法
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

## todo https://playwright.dev/python/docs/test-runners#examples

# 开始
## 安装
pip install playwright==1.25.2  

安装会自动下载浏览器，查看方式：  
- %USERPROFILE%\AppData\Local\ms-playwright on Windows
- ~/Library/Caches/ms-playwright on MacOS
- ~/.cache/ms-playwright on Linux

## 用法
```
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(executable_path='/Users/chenhaiou/Library/Caches/ms-playwright/chromium-844399/chrome-mac/Chromium.app/Contents/MacOS/Chromium')
    page = browser.new_page()
    page.goto("https://www.baidu.com/")
    browser.close()
```
