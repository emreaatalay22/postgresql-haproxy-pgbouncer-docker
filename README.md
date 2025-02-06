## README.md

# PostgreSQL HA Yapısı Docker Compose ile Kurulumu

Bu repo, PostgreSQL'i HAProxy ve PgBouncer kullanarak yüksek erişilebilirlik (High Availability - HA) modunda çalıştırmak için Docker Compose konfigürasyonunu içerir. Ek olarak Prometheus, Grafana ve JMeter entegrasyonlarıyla izleme ve performans testi desteği sağlar.

## İçerik
- **PostgreSQL Master & Replicas**: 1 ana ve 2 replika sunucu
- **PgBouncer**: PostgreSQL bağlantı yöneticisi
- **HAProxy**: Yük dengeleme ve yüksek erişilebilirlik
- **Grafana & Prometheus**: PostgreSQL performans izleme
- **JMeter**: Performans testi için entegre çalışma

## Kurulum

1. **Docker ve Docker Compose'un yüklü olduğundan emin olun**
   ```sh
   docker --version
   docker-compose --version
   ```
2. **Projeyi klonlayın**
   ```sh
   git clone https://github.com/kullaniciadi/postgresql-haproxy-pgbouncer-docker.git
   cd postgresql-haproxy-pgbouncer-docker
   ```
3. **Docker Compose ile sistemi başlatın**
   ```sh
   docker-compose up -d
   ```
4. **Servisleri kontrol edin**
   ```sh
   docker ps
   ```
5. **Grafana'ya erişim**
   - URL: [http://localhost:3000](http://localhost:3000)
   - Kullanıcı: `admin`, Parola: `admin`

6. **PostgreSQL Bağlantı Bilgileri**
   - Master: `localhost:5435`
   - Replica1: `localhost:5436`
   - Replica2: `localhost:5437`
   - PgBouncer: `localhost:6432`
   - HAProxy: `localhost:5432`

## Monitoring

### Prometheus Konfigürasyonu
Prometheus ile HAProxy, PgBouncer ve PostgreSQL metriklerini izleyebilirsiniz.

- Prometheus UI: [http://localhost:9090](http://localhost:9090)

- Perfomans Test Metrikleri : 
https://docs.google.com/spreadsheets/d/16CLkHBl-rKxFxeUA5h_wS2ldBErzCMv2/edit?usp=sharing&ouid=116674202853143301244&rtpof=true&sd=true


![HTTP Statistics](https://drive.usercontent.google.com/download?id=1mwaeoNDJ7U9zuWQCKhq-1443ntXsFt7D&export=view&authuser=0)


### Logları Görmek
```sh
docker-compose logs -f
```

---

## Medium Yazısı
Ayrıntılı konfigürasyon ve açıklamalar için şu yazıya göz atabilirsiniz:
[HikariCP, HAProxy, PgBouncer ve PostgreSQL Konfigürasyonu](https://medium.com/@emreatalay22/hikaricp-haproxy-pgbouncer-ve-postgresql-konfig%C3%BCrasyonu-37722f0d7062)

