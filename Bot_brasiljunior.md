```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.support import expected_conditions as EC

```


```python
driver = webdriver.Chrome()
driver.get("https://id.brasiljunior.org.br/sign-in")
```


    ---------------------------------------------------------------------------

    SessionNotCreatedException                Traceback (most recent call last)

    Input In [6], in <cell line: 1>()
    ----> 1 driver = webdriver.Chrome()
          2 driver.get("https://id.brasiljunior.org.br/sign-in")
    

    File ~\anaconda3\lib\site-packages\selenium\webdriver\chrome\webdriver.py:69, in WebDriver.__init__(self, executable_path, port, options, service_args, desired_capabilities, service_log_path, chrome_options, service, keep_alive)
         66 if not service:
         67     service = Service(executable_path, port, service_args, service_log_path)
    ---> 69 super().__init__(DesiredCapabilities.CHROME['browserName'], "goog",
         70                  port, options,
         71                  service_args, desired_capabilities,
         72                  service_log_path, service, keep_alive)
    

    File ~\anaconda3\lib\site-packages\selenium\webdriver\chromium\webdriver.py:92, in ChromiumDriver.__init__(self, browser_name, vendor_prefix, port, options, service_args, desired_capabilities, service_log_path, service, keep_alive)
         89 self.service.start()
         91 try:
    ---> 92     super().__init__(
         93         command_executor=ChromiumRemoteConnection(
         94             remote_server_addr=self.service.service_url,
         95             browser_name=browser_name, vendor_prefix=vendor_prefix,
         96             keep_alive=keep_alive, ignore_proxy=_ignore_proxy),
         97         options=options)
         98 except Exception:
         99     self.quit()
    

    File ~\anaconda3\lib\site-packages\selenium\webdriver\remote\webdriver.py:277, in WebDriver.__init__(self, command_executor, desired_capabilities, browser_profile, proxy, keep_alive, file_detector, options)
        275 self._authenticator_id = None
        276 self.start_client()
    --> 277 self.start_session(capabilities, browser_profile)
    

    File ~\anaconda3\lib\site-packages\selenium\webdriver\remote\webdriver.py:370, in WebDriver.start_session(self, capabilities, browser_profile)
        368 w3c_caps = _make_w3c_caps(capabilities)
        369 parameters = {"capabilities": w3c_caps}
    --> 370 response = self.execute(Command.NEW_SESSION, parameters)
        371 if 'sessionId' not in response:
        372     response = response['value']
    

    File ~\anaconda3\lib\site-packages\selenium\webdriver\remote\webdriver.py:435, in WebDriver.execute(self, driver_command, params)
        433 response = self.command_executor.execute(driver_command, params)
        434 if response:
    --> 435     self.error_handler.check_response(response)
        436     response['value'] = self._unwrap_value(
        437         response.get('value', None))
        438     return response
    

    File ~\anaconda3\lib\site-packages\selenium\webdriver\remote\errorhandler.py:247, in ErrorHandler.check_response(self, response)
        245         alert_text = value['alert'].get('text')
        246     raise exception_class(message, screen, stacktrace, alert_text)  # type: ignore[call-arg]  # mypy is not smart enough here
    --> 247 raise exception_class(message, screen, stacktrace)
    

    SessionNotCreatedException: Message: session not created: This version of ChromeDriver only supports Chrome version 105
    Current browser version is 107.0.5304.107 with binary path C:\Program Files\Google\Chrome\Application\chrome.exe
    Stacktrace:
    Backtrace:
    	Ordinal0 [0x0075DF13+2219795]
    	Ordinal0 [0x006F2841+1779777]
    	Ordinal0 [0x0060423D+803389]
    	Ordinal0 [0x006264AC+943276]
    	Ordinal0 [0x006219F0+924144]
    	Ordinal0 [0x0061F179+913785]
    	Ordinal0 [0x006536B9+1128121]
    	Ordinal0 [0x0065331A+1127194]
    	Ordinal0 [0x0064E616+1107478]
    	Ordinal0 [0x00627F89+950153]
    	Ordinal0 [0x00628F56+954198]
    	GetHandleVerifier [0x00A52CB2+3040210]
    	GetHandleVerifier [0x00A42BB4+2974420]
    	GetHandleVerifier [0x007F6A0A+565546]
    	GetHandleVerifier [0x007F5680+560544]
    	Ordinal0 [0x006F9A5C+1808988]
    	Ordinal0 [0x006FE3A8+1827752]
    	Ordinal0 [0x006FE495+1827989]
    	Ordinal0 [0x007080A4+1867940]
    	BaseThreadInitThunk [0x75236939+25]
    	RtlGetFullPathName_UEx [0x77508FD2+1218]
    	RtlGetFullPathName_UEx [0x77508F9D+1165]
    



```python
driver.find_element(By.XPATH,
    '//*[@id="__next"]/div/div/div/div/div[1]/div/div[1]/form/div[1]/div[1]/input').send_keys("147.682.066.03")
driver.find_element(By.XPATH,
    '//*[@id="__next"]/div/div/div/div/div[1]/div/div[1]/form/div[2]/div[1]/input').send_keys("riquegalvao")
driver.find_element(By.XPATH,
    '//*[@id="__next"]/div/div/div/div/div[1]/div/div[1]/form/div[3]/button').send_keys(Keys.ENTER)
```


```python

driver.get("https://portal.brasiljunior.org.br/ejs/equalitas-ufmg-consultoria-jr/coletas-de-metricas/10")
driver.find_element(By.XPATH,'//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[1]/div/div[2]/button').send_keys(Keys.CLICK)
driver.get("https://portal.brasiljunior.org.br/ejs/equalitas-ufmg-consultoria-jr/coletas-de-metricas/10")
try:
    botton = driver.find_element(By.XPATH,'//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[1]/div/div[2]/button')
    botton.send_keys(Keys.CLICK)
except NoSuchElementException:
    print("exception handled")
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[3]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[4]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[5]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[5]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[6]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[7]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[8]/div/div[1]/button[1]/spann').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[9]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[10]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[11]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[12]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[13]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[14]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[15]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[15]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[16]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[17]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[18]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[19]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[20]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[21]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[22]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[22]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[24]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[24]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[26]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[27]/div/div[1]/button[6]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[28]/div/div[1]/button[1]/span').send_keys(Keys.ENTER)
driver.find_element(By.XPATH,
    '//*[@id="ttz_body"]/div[4]/div/div/div/div/div/div[29]/div/div[2]/div/a').send_keys(Keys.ENTER)
```


```python

```
