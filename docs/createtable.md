# Cədvəl üzrə əməliyyatlar
## Cədvəl(Table) nədir? Niyə ehtiyyac duyuruq cədvəllərə?

Əvvəl də qeyd etdiyimiz kimi məlumatların saxlanılmasında əsas və yeganə rolu cədvəllər(Table) oynayır.Məlumatlar cədvəllərdə sətirlər(row/record) şəklində saxlanılır.Belə ki biz Cədvəllərdə sadə və əlaqəli məlumatları saxlayırıq.

Yaxşı bəs cədvəllər üzrə əməliyyatlar deyəndə nə nəzərdə tuturuq? Bu biraz fikir qarışdıran məsələdir.Yəni DML(Data Manipulation Language) və DDL(Data Definition Language) üzrə yanaşa bilərik.Biz bugun DDL əməliyyatları üzrə cədvəllər üzrə əməliyyat aparacağıq.

Ümumilikdə Sql Serverdəki məliyyatları aşağıdakı bölmələrə ayıra bilərik.

### DDL     -   Data Definition Language

<blockquote>Bu bölməyə aid olan komandaları misal göstərə bilərik.

- CREATE    – Verilənlər bazası və ya serverdə obyektlərin yaradılması üçün istifadə edirik.
- ALTER     – Verilənlər bazası və ya serverdə obyektlərin vəziyyətini dəyişmək üçün istifadə olunur.
- DROP      – Verilənlər bazasından və ya serverdən seçilmiş obyekti silir.
- TRUNCATE  – Cədvəldəki məlumatları tam silər və cədvəli ilk yaradıldığı vəziyyətə gətirir,hazırki sxemasinı tətbiq edərək.
- RENAME    – Obyektin adını dəyişmək üçün istifadə olunur.
</blockquote>

### DML     -   Data Manipulation Language   

<blockquote>Bu bölməyə aid olan komandaları misal göstərə bilərik.

- SELECT    – Cədvəllərdən məlumat oxumaq üçün istifadə edilir.
- INSERT    – Cədvələ məlumat əlavə etmək üçün istifadə edilir.
- UPDATE    – Cədvəldəki məlumat üzrə məlumat dəyişikliyi etmək üçün istifadə olunur.
- DELETE    – Cədvəldən məlumatları silər.
- MERGE     – Eyni anda insert,update,delete əməliyyatlarının hamısını icra etmək üçün istifadə edirik.
</blockquote>

### DCL     -   Data Control Language

<blockquote>Bu bölməyə aid olan komandaları misal göstərə bilərik.

- GRANT     – İstifadəçiyə hər hansı hüququn verilməsini təmin edir.
- DENY      – İstifadəçinin sahib olduğu və ya qrup sayəsində aldığı hüququ məhdudlaşdırır.
- REVOKE    – Adı çəkilən hüququ istifadəçiyə görə neytrallaşdırır.
</blockquote>

### TCL     -   Transaction Control Language

<blockquote>Bu bölməyə aid olan komandaları misal göstərə bilərik.

- COMMIT    – Tranzaksiyanın bitməsini qeyd edir və əmaliyyatları təsdiqləyir.  
- SAVEPOINT – Tranzaksiya daxilində qayıdıla biləcək bir nöqtə təyin edir.  
- ROLLBACK  – Sonuncu **COMMİT**`ə qədər icra edilən əməliyyatları ləğv edir.
</blockquote>


## Cədvəl yaratmaq üçün nə etməli?

Yuxarıdakı ətraflı məlumatdan sonra necə yeni bir cədvəl yarada bilərik ondan danışaq.İlk öncə yadda saxlamaq lazımdır ki, vasitəsi ilə visual şəkildə edə biləcəyimiz hər şey kimi, yeni cədvəli də visual şəkildə yatarmaq olar.Həmçinin eyni işi TSQL - kodları vasitəsi ilə də bunu icra edə bilərik.Misal üçün  <b>Category</b> cədvəlini gəlin daha öncə yatarmış olduğumuz <b>Intelect</b> verilənlər bazasında yaradaq.


```html
    use [Intelect];
    go
    CREATE TABLE Category(
        Id int,
        Name varchar(150)
    );
    go
```

Burdakı kodu oxumağa çalışsaq görəcəyikki kateqoriyaları qeyd etmək üçün <b>Category</b> adlı bir cədvəl yaradaraq kateqoriyanın <b id="modify">sıra nömrəsi (<em>Id</em>)</b> və <b>adını (<em>Name</em>)</b> qeyd etmək üçün sahələr ayırmışıq.Və informasiya sisteminin genişliyindən asılı olaraq bu sahələr arta bilər.Data strukturunun dəyişdirilib artırılması qərarını aldıqda isə biz rahat şəkildə T-SQL kodları vasitəsi bunu aşağıdakı kimi icra edə bilərsiz.

```html
    use [Intelect];
    go
    ALTER TABLE Category
    ADD SubName varchar(200);
    go
```

Beləliklə mövcud olan <b>Category</b> cədvəlinə <b>SubName</b> sütununu(column) əlavə etdik.

Və ya əksinə cədvəldə mövcud sütunu silə bilərik.Lakin bu qərarı verərkən ətraflı yoxlamaq lazımdır.Məlumat itkisi olmadığı halda bu əməliyyatı edə bilərik.


```html
    use [Intelect];
    go
    ALTER TABLE Category
    DROP COLUMN SubName;
    go
```


Biraz öncə əlavə etdiyimiz sütununu(column) cədvəldən sildik.

Yaxud da cədvəlin sütunları üzərində dəyişiklik edə bilərik.Misal üçün <b>Name</b> sütununun məlumat tipini dəyişərək <b>unicode tipli</b> məlumatlar qeyd edə bilməmiz üçün şərait yaradırıq.


```html
    use [Intelect];
    go
    ALTER TABLE Category
    ALTER COLUMN Name nvarchar(150);
    go
```

