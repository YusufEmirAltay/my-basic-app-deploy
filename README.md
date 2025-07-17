##  Proje Amacı

Bu proje, Git üzerinden yapılan kod değişikliklerini otomatik olarak Docker imajına dönüştüren, Helm Chart güncelleyen ve Argo CD ile Minikube kümesine dağıtan bir CI/CD hattı kurmayı amaçlar.

---

##  Gereksinimler

- Tüm kaynaklar (uygulama kodu, Helm Chart, ArgoCD manifesti) tek Git deposunda yer alır.
- main branch’e push edildiğinde CI pipeline tetiklenir.
- Pipeline adımları:
  - Docker imajı build edilir, SHA tag’i ile container registry’ye push edilir.
  - Helm Chart’ta image tag güncellenir, değişiklik commitlenir.
  - ArgoCD bu değişikliği algılar ve Minikube ortamına otomatik deploy eder.
- Pipeline içinde:
  - Testler (unit/integration) çalıştırılır.
  - Güvenlik taraması yapılır (Trivy vb.).
  - Başarı/başarısızlık durumuna göre Slack/e-posta bildirimi gönderilir.

