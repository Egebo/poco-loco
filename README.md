<div align="center">
  <img src="images/logo.jpg" alt="Poco Loco logo" width="220">

  # Poco Loco E-Ticaret Platformu

  Butik bir çanta markası için sıfırdan geliştirdiğim, canlı ödeme alan uçtan uca e-ticaret sitesi.

  **[poco--loco.com](https://poco--loco.com) adresinde yayında**
</div>

---

> **Not:** Bu bir müşteri projesidir; kaynak kodu müşteriye ait olduğu için bu repo yalnızca projeyi tanıtım amaçlıdır. Teknik detayları ve mimari kararları aşağıda bulabilirsiniz.

## Proje Hakkında

Poco Loco, butik bir çanta markasının tüm satış operasyonunu yürüten gerçek bir üretim (production) uygulamasıdır: ürün kataloğu, sepet, gerçek kart ödemesi, sipariş ve kargo takibi, promosyon kodları ve tam kapsamlı bir yönetim paneli.

## Öne Çıkan Özellikler

- 💳 **Uçtan uca ödeme:** iyzico entegrasyonu ile gerçek kart ödemesi; sipariş oluşturma ve ödeme callback akışı sunucu tarafında Supabase Edge Functions üzerinde çalışır
- 📦 **Sipariş & kargo takibi:** sipariş sonrası e-posta bildirimi, kargo durumu takibi
- 🏷️ **Promosyon kodları:** kullanım limiti ve son kullanma tarihi kontrolü ile indirim mantığı
- 🛠️ **Yönetim paneli:** ürün, sipariş ve içerik yönetimi için ayrı admin arayüzü; Excel'e fatura/sipariş dışa aktarma
- 🌐 **Çift dil:** i18next ile TR/EN arayüz

## Mimari

```
React 18 + TypeScript (Vite)
        │
        ├── UI: Tailwind CSS + shadcn/ui
        ├── Durum/veri: React Query · form: react-hook-form + zod
        │
        └── Supabase
              ├── PostgreSQL (ürün, sipariş, kullanıcı verisi)
              ├── Auth
              └── Edge Functions
                    ├── create-order
                    ├── iyzico-callback
                    ├── send-order-notification
                    └── notify-contact
```

Ödeme ve bildirim gibi güvenlik gerektiren tüm mantık istemciden ayrıştırılıp Edge Functions'a taşınmıştır; istemci hiçbir zaman ödeme sağlayıcısıyla doğrudan konuşmaz.

## Teknolojiler

| Katman | Teknoloji |
|---|---|
| Frontend | React 18, TypeScript, Vite, Tailwind CSS, shadcn/ui |
| Veri & form | React Query, react-hook-form, Zod |
| Backend | Supabase (PostgreSQL, Auth, Edge Functions) |
| Ödeme | iyzico |
| i18n | i18next (TR/EN) |
| Dağıtım | Vercel + Cloudflare |

## Süreç

~6 haftalık aktif geliştirme sürecinde 240'ın üzerinde commit ile yayına alındı; gerçek müşteri siparişleriyle canlıda çalışıyor.

---

<div align="center">
  <sub>Geliştirici: <a href="https://egebo.github.io">Egemen Bozca</a></sub>
</div>
