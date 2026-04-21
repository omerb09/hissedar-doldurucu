# Hissedar Toplu Doldurma

Kobasis bağış formundaki hissedar alanlarını Excel'den kopyala-yapıştır ile tek tıkta dolduran bookmarklet ve kurulum sayfası.

## Ne işe yarar?

`kobasis.hyrdm.org/bagis` sayfasında birden fazla hissedar girilirken tek tek yazmak yerine:

1. Excel'de **Ad Soyad** ve **Telefon** kolonlarını seç, kopyala.
2. Yer imlerindeki **Hissedar Doldur** butonuna bas.
3. Açılan kutuya yapıştır, **Doldur**'a bas.

Telefon formatı (boşluk, parantez, başındaki `0`) otomatik temizlenir, 10 haneye indirilir; sayfadaki input maskesi geri kalanını halleder.

## Kurulum

`index.html` dosyasını aç (ya da host edildiği adresi ziyaret et) ve sayfadaki butonu tarayıcının yer imleri çubuğuna sürükle-bırak.

Chrome/Edge'de yer imi çubuğu: `Ctrl+Shift+B` (Mac: `Cmd+Shift+B`).

## Güvenlik

- Bookmarklet tamamen tarayıcıda çalışır, hiçbir dış sunucuya istek atmaz.
- `location.hostname` kontrolüyle sadece `kobasis.hyrdm.org` üzerinde aktifleşir; başka sekmede tıklanırsa uyarı verip çıkar.
- Kurulum sayfası da Google Fonts vb. dış kaynaklara bağımlı değildir.

## Geliştirme

Tek dosyalık bir proje: `index.html`.

- Raw bookmarklet JS'i sayfadaki `<script type="text/plain" id="bookmarklet-src">` bloğunda okunur halde durur.
- Sayfa yüklenirken alttaki aktivasyon script'i `VERSION` sabitini tek yerden okuyup
  (a) `[data-version]` işaretli her elemente yazar, (b) JS'i `encodeURIComponent` ile
  encode edip `.bookmarklet-btn` anchor'ının `href`'ine bağlar.
- Bookmarklet JS'inde `__VERSION__` placeholder'ı runtime'da gerçek sürümle değişir.

Yeni sürüm çıkarmak için aktivasyon script'indeki `var VERSION = 'v1.x'` satırını değiştir,
git tag at. Panel başlığı, HTML rozeti ve FAQ'teki örnek otomatik senkron olur.

## Sürüm

Git tag'leri otoritedir. En son sürümü `git tag -l | sort -V | tail -1` ile gör.
