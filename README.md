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

Tek dosyalık bir proje: `index.html`. Bookmarklet kaynağı, dosyanın içindeki `<a class="bookmarklet-btn" href="javascript:...">` bağlantısının href'inde URL-encode edilmiş şekilde durur.

Bookmarklet'i güncellemek için:

1. JS kaynağını ayrı bir dosyaya çıkar, düzenle.
2. `node -e "console.log('javascript:'+encodeURIComponent(require('fs').readFileSync('src.js','utf8').replace(/\n/g,'')))"` ile encode et.
3. Sonucu `href="..."` değeri olarak yerleştir.
4. Panelin başlığındaki sürüm etiketini (`v1.0`) bir adım artır ki kullanıcılar hangi sürümü kullandıklarını görsün.

## Sürüm

Bookmarklet içi sürüm: **v1.0**
