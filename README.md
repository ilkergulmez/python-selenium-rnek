# python-selenium-ornek
python selenium ile otomatik whatsapp mesajları gönderin
Bu projede selenium kütüphanesi ve birkaç yardımcı kütüphane ile daha önceden tanımladığımız numaralara otomatik olarak belirlediğimiz 
mesajları gönderebileceğiz. 
projedeki gereksimlerin şu şekildedir.
- İDE (PYCHARM VEYA CODE OLABİLİR)
- PİP ARACILIĞI İLE GEREKLİ KÜTÜPHANELERİ YÜKLEMENİZ GEREKİR.
- GECKODRIVER YANİ TARAYICI İÇİN ORTAM HAZIRLAYAN KÜÇÜK BİR PROGRAM

ve sonuç olarak programı çalıştırın python sizin yerinize yüzlerece kişiye mesajları atsın.

import time
from selenium import webdriver
import pyautogui
from selenium.webdriver.common.by import By

geckodriver = webdriver.Firefox()
geckodriver.get("https://www.google.com")
print ("Açılış sayfanız tanımlı olarak google dir")
input("devam etmek için bir tuşa basınız")
web = input("giriş yapmak istediğiniz web siteyi belirtiniz : ")
if (web == "whatsapp"):
    geckodriver.get("https://web.whatsapp.com")
    time.sleep(2)
    print("web whatsapp QR kodu okutup devam edebilirisiniz")
else:
    geckodriver.get("https://www.google.com")
input ("Tanımlı numaralara Toplu mesaj atmak için enter tuşuna basmanız yeter :)) ")

numbers = {5350000000,5360000000,}
mesaj = "buraya mesaj içeriği yazılacak"
for i in numbers:
    numbers = geckodriver.find_element(By.XPATH, "/html/body/div[1]/div[1]/div[1]/div[3]/div/div[1]/div/label/div/div[2]").send_keys(i)
    pyautogui.press("enter")
    mesajAlani = geckodriver.find_element(By.XPATH, "/html/body/div[1]/div[1]/div[1]/div[4]/div[1]/footer/div[1]/div/span[2]/div/div[2]/div[1]/div/div[2]").send_keys(mesaj)
    pyautogui.press("enter")
    time.sleep(2)

