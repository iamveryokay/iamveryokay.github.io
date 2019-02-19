Title: Python Selenium使用Geckodriver访问网页
Date: 2019-02-19
Category: Python
Tags: Python, Selenium, Firefox, Geckodriver

# 配置环境
* Geckodriver: 0.23.0
* Selenium: 3.141.0
* Python: 3.6.6

# 代码
```python
from selenium import webdriver
from selenium.webdriver.common.proxy import Proxy, ProxyType
from selenium.webdriver.firefox.options import Options
from selenium.webdriver.common.keys import Keys

geckodriver_path = '/path-to-/geckodriver'
req_url = 'http://xxx.com'

options = Options()
# options.log.level = 'trace'  # for debug
# options.headless = True 

# ----- if you need a proxy
# my_proxy = 'http://xxx.com:8080'  
# proxy = Proxy({
#            'proxyType': ProxyType.MANUAL,
#            'httpProxy': my_proxy,
#            'ftpProxy': my_proxy,
#            'sslProxy': my_proxy,
#            'noProxy': ''
#        })
# driver = webdriver.Firefox(executable_path=geckodriver_path, options=options,
#                            proxy=proxy)

driver = webdriver.Firefox(executable_path=geckodriver_path, options=options)

username_box = driver.find_element_by_id('username')
password_box = driver.find_element_by_id('password')
username_box.send_keys('uid')
password_box.send_keys('password')
password_box.send_keys(Keys.RETURN)

import time
time.sleep(3)  # This step is very important
cookie = driver.get_cookies()

driver.close()
driver.quit()

```

# 感想
不用chromedriver的原因是它用插件代理的情况下不能使用headless模式。

那个睡三秒坑了我好久，原因是如果不睡的话，就会导致在没有获取到部分cookies然后就退出了，导致无法正常登陆。拿全cookies就可以上requests来操作了，爽歪歪～