# Unix üzerinde nasıl kurulum yapılır ve çalıştırılır? (Linux, macOs)
* Terminali çalıştırın.
```
pip install -U instabot
git clone https://github.com/instagrambot/instabot --recursive
cd instabot/examples
```
* Ve sonrasında aşağıdaki gibi kolaylıkla çalıştırabilirsiniz.
```
python multi_script_CLI.py
```

## Hatalar

* Eğer `pip: command not found` hatası alırsanız, aşağıdaki kod satırını deneyin:
```
sudo easy_install pip
```

* Eğer `pip install -U instabot` yaptığınız sırada `permission denied` hatası alırsanız, aşağıdaki kod satırını deneyin:
```
sudo pip install -U instabot
```

* Eğer `sudo pip install -U instabot` komutu sırasında hala `permission denied` hatası alıyorsanız, aşağıdaki kod satırını deneyin:
```
sudo -H pip install -U instabot
```
