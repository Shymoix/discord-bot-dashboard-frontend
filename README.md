# Discord Bot Dashboard (Frontend Only)

Bu proje, **Nuxt 3** ile geliştirilmiş sadece arayüz (frontend) kısmından oluşan bir Discord bot dashboard tasarımıdır. Henüz veri çekme, API bağlantısı veya backend entegrasyonu içermemektedir.

## 📁 Sayfalar ve Amaçları

- **`/` (index)**  
  Ana sayfa. Dashboard’a giriş noktasıdır, genel bilgilendirme ve yönlendirmeler içerebilir.

- **`/moderation`**  
  Sunucudaki kullanıcılar üzerinde yapılabilecek moderasyon işlemleri için tasarlanmış sayfadır (kick, ban, timeout vb.).

- **`/admin`**  
  Yönetici panelidir. Dashboard ayarları, bot yönetimi gibi işlemler için tasarlanmıştır.

- **`/guild`**  
  Kullanıcının sunucularının (guild) listelendiği, sunucu seçim işleminin yapılabileceği sayfadır.

- **`/fun`**  
  Eğlenceli komutlara veya özelliklere ait bileşenlerin bulunduğu sayfadır. Eğlence komutlarının arayüzü burada yer alır.

- **`/automod`**  
  Otomatik moderasyon kurallarını temsil eder. Spam, link engelleme vb. ayarların arayüzü buraya yerleştirilir.

## 🛠️ Teknolojiler

- [Nuxt 3](https://nuxt.com/)
- [Vue 3](https://vuejs.org/)
- [Tailwind CSS](https://tailwindcss.com/) (isteğe bağlı)
- (API veya backend **yoktur**)

## 🔧 Kurulum

Projeyi yerel ortamda çalıştırmak için:

```bash
# Depoyu klonlayın
git clone https://github.com/kullaniciadi/discord-dashboard.git
cd discord-dashboard

# Bağımlılıkları yükleyin
npm install

# Geliştirme sunucusunu başlatın
npm run dev
```
