# 🚀 mCore - Advanced Server Core

![Version](https://img.shields.io/badge/version-4.5-blue.svg?style=for-the-badge)
![Java](https://img.shields.io/badge/Java-17%2B-orange.svg?style=for-the-badge)
![Software](https://img.shields.io/badge/Software-Paper%20%2F%20Spigot-red.svg?style=for-the-badge)

**mCore**, Minecraft sunucunuzun temel ihtiyaçlarını karşılayan, yüksek performanslı ve modern bir çekirdek (core) eklentisidir. İçerisinde gelişmiş TPA sistemleri, 1v1 Eşleşme (RTP Queue), Combat Log koruması ve Admin araçları barındırır.

---

## 🌟 Öne Çıkan Özellikler

* **Multi-Event TPA Sistemi (v4.5):** Aynı anda birden fazla yetkili, kendi özel etkinliklerini oluşturabilir. Oyuncular karışıklık olmadan dilediği yetkilinin etkinliğine katılabilir.
* **Gelişmiş RTP (Rastgele Işınlanma):**
    * **Queue (Sıra):** Oyuncular sıraya girer ve sistem onları eşleştirip rastgele bir konuma atar.
    * **Duel (Düello):** Oyuncular birbirine istek atarak 1v1 için uzak bir konuma ışınlanır.
* **Modern GUI Menüler:** TPA ve Düello istekleri, tamamen özelleştirilebilir menüler (GUI) üzerinden yönetilir.
* **Combat Log:** Savaştan kaçışları engeller, oyundan çıkanları cezalandırır.
* **HEX Renk Desteği:** Tüm mesajlarda modern renk kodları (Gradient, RGB) desteklenir.

---

## ⚙️ Kurulum

1.  `mCore-4.5.jar` dosyasını sunucunuzun `plugins` klasörüne atın.
2.  Sunucuyu yeniden başlatın.
3.  `config.yml`, `messages.yml` ve `menus` klasörünün oluştuğundan emin olun.

### Gereksinimler
* **Java:** 17 veya üzeri.
* **Soft Depend:** `PlaceholderAPI`, `Vault` (Önerilir).

---

## 🛡️ Komutlar ve Yetkiler

### 👑 Yönetici Komutları

| Komut | Yetki | Açıklama |
| :--- | :--- | :--- |
| `/mcore` | `mcore.admin` | Eklenti dosyalarını (Config, Lang, Menü) yeniler. |
| `/gmc`, `/gms`, `/gmsp` | `mcore.gamemode` | Oyun modunu değiştirir. |
| `/fly [oyuncu]` | `mcore.fly` | Uçuş modunu açar/kapatır. |
| `/walkspeed <1-10>` | `mcore.speed` | Yürüme hızını ayarlar. |
| `/flyspeed <1-10>` | `mcore.speed` | Uçuş hızını ayarlar. |
| `/lightning [oyuncu]` | `mcore.lightning` | Şimşek çaktırır. |
| `/sudo <oyuncu> <komut>` | `mcore.sudo` | Başka bir oyuncu adına işlem yapar. |
| `/playerinfo <oyuncu>` | `mcore.playerinfo` | Oyuncu bilgilerini (IP, UUID, Konum) gösterir. |
| `/alts <oyuncu>` | `mcore.alts` | Oyuncunun yan hesaplarını (IP bazlı) tarar. |
| `/clearchat` | `mcore.clearchat` | Sohbeti temizler. |

### 👤 Oyuncu Komutları

| Komut | Yetki | Açıklama |
| :--- | :--- | :--- |
| `/tpa <oyuncu>` | Yok | Işınlanma isteği gönderir. |
| `/tpahere <oyuncu>` | Yok | Yanına çekme isteği gönderir. |
| `/tpacancel` | Yok | Gönderilen isteği iptal eder. |
| `/tpaevent` | `mcore.tpaevent` | (Admin) Etkinlik başlatır, (Oyuncu) Etkinliğe katılır. |
| `/rtpqueue` | Yok | 1v1 Rastgele Işınlanma sırasına girer. |
| `/rtpduel <oyuncu>` | Yok | Belirli bir oyuncuya düello isteği atar. |
| `/back` | `mcore.back` | Ölmeden veya ışınlanmadan önceki son konuma döner. |

---

## 🔧 Yapılandırma (Config)

### `config.yml` Örneği

```yaml
prefix: "<bold><gradient:#29f057:#41f06a>mCore</gradient></bold> <dark_gray>»</dark_gray> "

# Savaş Koruması
combat-log:
  enabled: true
  duration: 15 # Saniye
  kill-on-quit: true # Çıkarsa öldür
  whitelisted-worlds:
    - "spawn"

# TPA Ayarları
tpa:
  timeout: 60
  delay: 3
  sound-on-request: "BLOCK_NOTE_BLOCK_PLING"

# RTP (Rastgele Işınlanma)
rtp-queue:
  world: "sand"
  min-range: 100
  max-range: 2000
  distance-between-players: 8.0
  timeout-seconds: 96
  command: "kit1" # Işınlanınca verilecek kit/komut

# Kill Efektleri
kill-system:
  enabled: true
  title:
    enabled: true
    main: ""
    sub: "<green>+1 Kill</green>"
