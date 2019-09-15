# MsSql
Verilənlər Bazası(VB) = DataBase (DB)

- [Db əməliyyatları](/docs/database.md)
  - Db yaratmaq
  - Db adını dəyişmək və silmək

- Cədvəl üzrə əməliyyatlar
  - [Verilənlərin tipləri - DataTypes](/docs/datatypes.md)
  - Düzgün data tipinin seçilməsi
  - [Yeni cədvəl yaratmaq](/docs/createtable.md)
  - [Cədvəlin strukturunun dəyişdirilməsi və cədvəlin silinməsi](/docs/createtable.md#modify)
  - [Məhdudlaşdırıcılar - Constraints](/docs/constraints.md)
    - [Default və Not Null məhdudlaşdırıcıları](/docs/constraints.md#notnull)
    - [Təkrarların məhdudlaşdırılması (Unique Key)](/docs/constraints.md#uniquekey)
    - [Əsas açar (Primary Key)](/docs/constraints.md#primarykey)
    - [Şərt məhdudlaşdırıcısı (Check Constraints)](/docs/constraints.md#check)
    - [Xarici açar məhdudlaşdırıcısı (Foreign Key Constraints)](/docs/constraints.md#foreignkey)

- T-Sql İfadələri
  - [Qeydiyyat ifadələri](/docs/dml.md)
    - [Yeni məlumat əlavə etmək](/docs/dml.md#insert)
    - [Mövcud məlumat üzrə dəyişiklik etmək](/docs/dml.md#update)
    - [Mövcud məlumatı silmək](/docs/dml.md#delete)
  - [Seçim ifadələri](/docs/dql.md)
    - [Məlumatların şərtlərə görə seçilməsi](/docs/dql.md#search1)
    - [Təkrarsız məlumatların seçilməsi](/docs/dql.md#distinct)
    - [Məlumatların fərqli göstəricilərinə görə sıralanması](/docs/dql.md#order)
    - [Limitli seçmə ifadələri](/docs/dql.md#top)
    - [Şərti adların istifadə edilməsi](/docs/dql.md#alias)
    - [Məlumatların səhifə şəklində seçilməsi](/docs/dql.md#paging)
  - [Qoşma operatorları](/docs/join.md)
    - [Inner join](/docs/join.md#innerjoin)
    - [Left join](/docs/join.md#leftjoin)
    - [Right join](/docs/join.md#rightjoin)
    - [Full join](/docs/join.md#fulljoin)

- Sql Operatorları
  - IN
  - BETWEEN
  - ANY
  - ALL
  - SOME
  - EXISTS

- Sql Funksiyaları
  - Skalar Funksiyalar (Scalar-Valued) / UPPER(),LOWER(),LEN(),ROUND(),GETDATE()
  - Cədvəl qaytaran funsiyalar (Table-Valued)
  - Agreqat (Aggregate) funksiyaları / AVG(),SUM(),COUNT(),MAX(),MIN()
  - Gruplama ifadələri / GROUP BY, HAVING
  - Bəzi vacib funksiyalar
    - CONVERT(),CAST(),PARSE()
    - TRY_CONVERT(),TRY_PARSE()
    - CONCAT()
    - FORMAT()
    - IIF(),CHOOSE()
    - EOMONTH()
  - Yeni funksiyanın yaradılması,redaktə edilməsi və silinməsi
  
- Sql-də Prosedurlar
  - Yeni prosedur yaratmaq
  - Prosedurun çağırılması
  - Proseduru yeniləmək və silmək

- Sql-də View-lər
  - Yeni view yaratmaq və istifadə etmək
  - Viewlərin redaktəsi və silinməsi
  - Check Option, Encrpytion,Schemabinding təyinləri

- Sql-də Triggerlər
  - Yeni trigger yaratmaq və istifadə etmək
  - Triggerlərin redaktəsi və silinməsi


----------------------------------------------------------------------------
- http://www.sqlservertutorial.net/sql-server-basics/sql-server-select/
- http://www.btdersleri.com/ders/Sql-Karşılaştırma-ve-Mantıksal-Operatörleri
- http://hrzafer.com/sql-dersleri
- http://www.java2s.com/Tutorial/SQLServer/CatalogSQLServer.htm
- https://www.yazilimkodlama.com/sql-server-2/sql-sorgulari-ve-ornekleri/
