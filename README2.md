# Zabbix Palo Alto Firewall API Monitoring Template

Bu şablon **Palo Alto firewall-larını API vasitəsilə Zabbix üzərindən monitorinq etmək** üçün hazırlanmışdır. Tamamilə skript yazmağa ehtiyac olmadan, bu şablonla Palo Alto cihazlarını A-dan Z-yə hər şeyi ilə monitorinq edə bilərsiniz.

## Niyə API ilə Monitorinq?

Ənənəvi olaraq SNMP geniş şəkildə istifadə olunur, lakin bəzi Palo Alto modelləri və versiyaları ilə uyğunluq problemləri yaşanır. SNMP ilə monitorinq zamanı boşluqlar meydana gələ bilər. Bu problemi aradan qaldırmaq üçün, Palo Alto-nun API interfeysi daha dəqiq və stabil monitorinq imkanı təqdim edir.

API, şəbəkə təhlükəsizliyi tədbirlərini və resursların performansını izləmək üçün daha çox məlumat əldə etməyə imkan verir.

## Xüsusiyyətlər

- **Tam əhatə:** Palo Alto firewall-larının performansını, resurslarını, interfeyslərini və təhlükəsizlik tədbirlərini API vasitəsilə monitorinq edin.
- **Skript yoxdur:** Bu şablon skriptə ehtiyac qalmadan, Zabbix üzərində asanlıqla quraşdırılıb istifadəyə verilir.
- **Yüksək dəqiqlik:** API ilə birbaşa əlaqə quraraq daha dəqiq məlumatlar əldə edin.
- **Versiya və model uyğunluğu:** SNMP ilə yaranan uyğunluq problemlərini API ilə aradan qaldırın.

## Tələblər

Bu şablondan istifadə etmək üçün aşağıdakı tələbləri yerinə yetirməyiniz lazımdır:

- **Palo Alto cihazı** (API dəstəkli olmalıdır)
- **Zabbix Server v6.0 və ya daha yeni**
- **Zabbix Agent**
- **API istifadəçi adı və şifrəsi**
- **Palo Alto API açarı**

## Quraşdırma

### Addım 1: Palo Alto cihazında API-nin aktivləşdirilməsi

1. Palo Alto firewall idarə panelinə daxil olun.
2. `Device` bölməsinə gedin.
3. Sol paneldən `Setup > Management > API Key Lifetime` parametrlərini yoxlayın və lazım gələrsə, aktiv edin.

### Addım 2: Zabbix-də Palo Alto cihazını əlavə edin

1. **Zabbix Web Interface**-ə daxil olun.
2. `Configuration > Hosts` bölməsinə gedin.
3. `Create Host` düyməsinə basın və Palo Alto cihazınızı əlavə edin:
   - Host adı: PaloAlto_Firewall
   - Host interfeysi: Palo Alto cihazınızın IP ünvanı
   - Template: **Palo Alto Firewall API Monitoring**

### Addım 3: Palo Alto API şablonunu əlavə edin

1. **Template** bölməsinə keçin (`Configuration > Templates`).
2. `Import` düyməsinə basın və bu şablon faylını yükləyin.
3. Şablonu cihazınıza tətbiq edin.

### Addım 4: API Açarını Zabbix-ə daxil edin

1. Palo Alto cihazınızdan API açarını əldə edin:
   ```bash
   curl -k -X POST "https://<firewall-ip>/api/?type=keygen&user=<username>&password=<password>"
