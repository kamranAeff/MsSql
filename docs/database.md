# Db əməliyyatları

## Verilənlər bazası nədir? Hansı Verilənlər bazası idarəetmə sistemləri var?

İnformasiya sistemi yaradılarkən məlumatların daimi olaraq saxlanılması şərti meydana gəlir.Bu zaman bizim verilənlər bazalarının idarə edilməsi sistemi seçimi etməmiz lazım gəlir.Hazırda verilənlər bazasının idarə etmə sistemləri kifayət qədərdir.Onlardan aşağıdakıları misal göstərmək olar.

- Microsoft SQL Server
- Oracle RDBMS
- IBM DB2
- MySQL
- Microsoft Access
- SQLite
- PostgreSQL
- MongoDB

bu siyahını beləcə uzada bilərik...

Biz tədris müddətində **Microsoft SQL Server 2016** versiyasını tədris edəcəyik və kurs müddətincə programlarımızda bu VB idarə etmə sistemindən istifadə edəcəyik.
Verilənlər bazası **server** və **client** səviyyəli olaraq iki yerə ayrılır.Yəni verilənlər bazaları mərkəzləşdirilmiş bir verilənlər bazası üçün təyin edilmiş serverdə saxlanılır və ona müraciət edən, client program olan [Sql Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) tərəfindən baza(bazalar) üzərində əməliyyatlar reallaşdırılır.

Server və management studio qurulduqdan sonra isə biz management studionu qoşub, serverə qoşulub informasiya sistemimiz üçün verilənlər bazası yaradırıq.Management Studio vasitəsi ilə həm vizual həm də t-sql commandlar vasitəsi ilə verilənlər bazası yarada bilərik.Verilənlər bazasının Tsql commandlar vasitəsi ilə yaradılması üçün aşağıdakı komandanı icra etməliyik.

```html
    use [master];
    go
    create database Intelect;
    go
```

Verilənlər bazasının adını da həmçinin dəyişə bilərik.Lakin bu tövsiyyə olunmur.Çünki resurs adları köhnə verilənlər bazasının adını əsas götürəcək.Aşağıdakı komandadan istifadə edərək bu əməliyyatı icra edə bilərik.


```html
    USE master;  
    GO  
    -- ALTER DATABASE <cari_db_adi> SET SINGLE_USER WITH ROLLBACK IMMEDIATE
    ALTER DATABASE Intelect SET SINGLE_USER WITH ROLLBACK IMMEDIATE
    GO
    -- ALTER DATABASE <cari_db_adi> MODIFY NAME = <yeni_db_adi> ;
    ALTER DATABASE Intelect MODIFY NAME = TestIntelect ;
    GO  
    --ALTER DATABASE <yeni_db_adi> SET MULTI_USER
    ALTER DATABASE TestIntelect SET MULTI_USER
    GO
```

həmçinin aşağıdakı sistem proseduru vasitəsi ilə bu prosesi icra edə bilərik.


```html
    USE master;  
    GO  
    -- EXEC sp_renamedb N'<cari_db_adi>', N'<yeni_db_adi>';  
    EXEC sp_renamedb N'TestIntelect', N'Intelect';  
    GO
```


Bəzən test müddətində yaratdığımız lazımsız bazaları silmək istəyə bilərik.O zaman aşağıdakı komandanı icra edirik.


```html
    USE master;  
    GO  
    drop database Intelect;	
    GO  
```

