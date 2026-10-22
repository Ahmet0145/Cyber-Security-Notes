# 🌐 OWASP Top 10 Overview & Risk Rating Methodology

## 1. What is OWASP?
**OWASP (Open Worldwide Application Security Project)**, web uygulaması güvenliğini artırmayı hedefleyen kâr amacı gütmeyen küresel bir topluluktur. 

OWASP Top 10 listesi, dünya genelindeki güvenlik uzmanları, istatistiki veri analizleri ve gerçek dünya zafiyet raporları bir araya getirilerek her birkaç yılda bir güncellenen en kritik 10 web güvenlik riskini temsil eder.

---

## 2. OWASP Risk Rating Methodology

OWASP, zafiyet risklerini değerlendirirken standart **Likelihood (Olasılık)** ve **Impact (Etki)** denklemine dayanır:

$$\text{Risk} = \text{Likelihood (Olasılık)} \times \text{Impact (Etki)}$$

### Risk Değerlendirme Faktörleri:

1. **Threat Agent Factors (Tehdit Aktörü Faktörleri):**
   - **Technical Skills:** Saldırganın gereken teknik beceri seviyesi.
   - **Motive:** Saldırganın motivasyonu (maddi, politik, zevk vb.).
   - **Opportunity:** Zafiyeti tespit etmek ve sömürmek için gereken erişim/fırsat.

2. **Vulnerability Factors (Zafiyet Faktörleri):**
   - **Ease of Discovery:** Zafiyeti bulmanın kolaylığı (otomatik tarayıcılar vs. manuel analiz).
   - **Ease of Exploit:** Zafiyeti sömürmenin (exploit etmenin) kolaylığı.
   - **Awareness:** Zafiyetin geliştirici ekibi/sektör tarafından bilinirliği.

3. **Technical Impact (Teknik Etki):**
   - **Loss of Confidentiality:** Gizlilik kaybı (Veri sızıntısı).
   - **Loss of Integrity:** Bütünlük kaybı (Veri değiştirme, veri silme).
   - **Loss of Availability:** Erişilebilirlik kaybı (Hizmet dışı bırakma - DoS).
   - **Loss of Accountability:** İzlenebilirlik kaybı (Logların yok edilmesi/sahtelenmesi).

4. **Business Impact (İş Etkisi):**
   - Finansal zarar, itibar kaybı, yasal yaptırımlar ve kişisel verilerin korunması (KVKK/GDPR) ihlalleri.

---

## 3. OWASP Top 10:2025 Standard vs. Previous Iterations

OWASP Top 10 listeleri zaman içinde evrilir. 2025 versiyonunda odağın kaydığı temel alanlar:
- **Supply Chain Security:** Üçüncü taraf kütüphane ve bağımlılıkların güvenlik süreçlerine entegrasyonu (A03:2025).
- **Insecure Architecture:** Kodlama hatalarından ziyade sistem mimarisi ve tasarım eksikliklerine odaklanılması (A06:2025).
- **Resilience & Exception Handling:** Hata yönetimi ve beklenmeyen durumların güvenli işlenmesi (A10:2025).
