# Instabot kullanıcı filresi nasıl yapılır?

Instabot'un, insanlara abone olmadan önce, bilinçli olarak aktif olmayan ve sahte bir izleyici kitlesine abone olmamak için onları filtrelediği bir sır değildir. Aşağıda, bu filtrasyonda uygulanan koşulların tam listesini bulacaksınız.

## Seçenekler

Başlangıçta, değiştirmekte özgür olduğunuz koşulları belirtmekte fayda var. Aşağıda, bot yapıcısının filtreleme ile ilgili parametrelerini vereceğim.

``` python
bot = Bot(max_likes_to_like=100,
          max_followers_to_follow=2000,
          min_followers_to_follow=10,
          max_following_to_follow=10000,
          min_following_to_follow=10,
          max_followers_to_following_ratio=10,
          max_following_to_followers_ratio=2,
          min_media_count_to_follow=3,
          stop_words=['shop', 'store', 'free'])
```
Bu değerleri kendinize göre değiştirmek istiyorsanız `bot = Bot()` betiğini kendi değerlerinize göre düzenleyerek kaydedin.

## Kullanıcı filtreleme

_Not_: True - takip edebilirsin, False - takip edemezsin.
* Eğer whitelist'te yer alıyorsa: True,
* Eğer blacklist'te yer alıyorsa: False,
* Eğer zaten takip ediyorsan: False,
* Eğer business hesabı ise: False,
* Eğer onaylı bir hesap ise: False,
* Eğer takipçi sayısı min_followers_to_follow 'dan az ise: False,
* Eğer takipçi sayısı max_followers_to_follow 'dan fazla ise: False,
* Eğer takip sayısı min_following_to_follow 'dan az ise: False,
* Eğer takip sayısı max_following_to_follow 'dan fazla ise: False,
* Eğer takip / takipçi oranı max_following_to_followers_ratio 'dan fazla ise: False,
* Eğer takipçi / takip sayısı max_followers_to_following_ratio 'dan fazla ise: False,
* Eğer gönderi sayısı min_media_count_to_follow 'dan az ise: False,
* Eğer açıklama kısmında stop_words listesinden içerikler yer alıyor ise: False,
* Eğer filtrelenmediyse: True.
