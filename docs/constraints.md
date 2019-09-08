# Məhdudlaşdırıcılar - Constraints

Məhdudlaşdırıcılar məlumatların tamlıq və bütünlüyünü qorumaq baxımından çox vacib anlayışlardandır. Məhdudlaşdırıcı ilə bir cədvəldə sütunun boş buraxılıb buraxılmadığını,verilmiş şərtlər daxilində olduğunu ya da başqa bir cədvəllə əlaqələrin tamlığının qorunmasını təmin edir.Məhdudlaşdırıcılar 5 qrupa bölünür

- Default və Not Null məhdudlaşdırıcıları
- Təkrarların məhdudlaşdırılması (Unique Key)
- Əsas açar (Primary Key)
- Şərt məhdudlaşdırıcısı (Check Constraints)
- Xarici açar məhdudlaşdırıcısı (Foreign Key Constraints)

<h2 id="notnull">Default və Not Null məhdudlaşdırıcıları</h2>
Bir öncəki dərslərdəki Category cədvəlinin koduna nəzər yetirək.

```html
    use [Intelect];
    go
    CREATE TABLE Category(
        Id int,
        [Name] nvarchar(150)
    );
    go
```

İndiki halda yeni məlumat əlavə etsək və <b>kateqoriya ad</b>ını boş buraxaraq yalnız <b>kod</b> əlavə edərək məlumat yarada bilərik.

```html
    use [Intelect];
    go
    insert into [Category]([Id]) values(1);
    go
```

və nəticəyə baxsaq 

```html
    use [Intelect];
    go
    select * from [Category];
    go
```

görərikki kategoriya adı boş olaraq qeyd olunub və bu yolverilməzdir.Ona görə də bu halların baş verməsinin qarşısını almalıyıq.Bunun üçün də <b>not null</b> məhdudlaşdırıcısından istifadə edirik.Yəni aşağıdakı kodla <b>Name</b> sütununun boç buraxıla bilinmiyəcək bir sütun oldugunu qəti olaraq təyin etmiş oluruq.

```html
    use [Intelect];
    go
    ALTER TABLE [Category] 
    ALTER COLUMN [Name] nvarchar(150) NOT NULL;
    go
```

yenidən bu kodu çağırası olsaq <b>Name</b> sütununun boş buraxılma icazəsi olmadığı barədə xəta alacayıq.

```
    use [Intelect];
    go
    insert into [Category]([Id]) values(1);
    go
```  
> Cannot insert the value NULL into column 'Name', table 'Intelect.dbo.Category'; column does not allow nulls. INSERT fails.

Bəzi hallarda isə boş buraxılması imkanı olmayan sütun üçün susmaya görə təyin etmək olar.Misal üçün sətrin yaradılma tarixi.Yəni əgər bizə maraqlıdırsa ki bu kateqoriya hansı tarixdə yaradılıb onda aşağıdakı kodla cədvələ əməliyyat tarixini qeyd etmək üçün yeni sütun əlavə edirik.Və eyni anda susmaya görə dəyərini vermək üçün **getdate()** funksiyasından istifadə edirik.

```
    use [Intelect];
    go
    ALTER TABLE [Category]
    ADD [CreatedDate] date NOT NULL DEFAULT getdate();
    go
```  

ya da əvvəlcədən mövcud bir sütuna DEFAULT Constraint əlavə edə bilərik
```
    use [Intelect];
    go
    ALTER TABLE [Category]
    ADD CONSTRAINT DK_CreatedDate DEFAULT getdate() FOR CreatedDate;
    go
```  

> İndi yeni sətir əlavə etsək görəcəyikki yeni yaratdığımız **CreatedDate** sütununu not null olaraq qeyd etdiyimizə baxmayaraq,onu qeyd etmədən yeni sətir insert etdikdə hec bir problemlə qarşılaşmadıq.

```
    use [Intelect];
    go
    insert into [Category]([Id],[Name]) values(2,N'Ofis Ləvazimatları');
    go
```  

Yuxarıdakı komandadan sonra cədvəldəki məlumatları yoxlasaq görəcəyikki əməliyyat tarixi avtomatik qeyd olunub.


<h2 id="uniquekey">Təkrarların məhdudlaşdırılması (Unique Key)</h2>

Təkrarlanmayan dəyərləri saxlayacaq sütunlara təyin ediləsi gərək olan məhdudlaşdırıcıdır. Misal üçün yuxarıdakı nümunəyə əsasən yenidən 

```
    use [Intelect];
    go
    insert into [Category]([Id],[Name]) values(2,N'Məişət Əşyaları');
    go
```  
məlumat əlavə etsək və id dəyərini eyni saxlasaq bu zaman anomaliya yaranacaq cədvəlimizdə.Yəni həm 'Məişət Əşyaları' həm də 'Ofis Ləvazimatları' adlı iki kateqoriyamızın hər ikisi eyni eyni koda sahib olacaqlar.Bu da yolverilməzdir.Ona gorə də əvvəcə test etdiyimiz cədvəlin icindəki məlumatları təmizləyib sonra məhdudlaşdırıcımızı əlavə edirik

```
    use [Intelect]
    TRUNCATE TABLE [Category]; --məlumatların tamamən silinməsi
    GO
    ALTER TABLE [Category]
    ADD CONSTRAINT  UCategoryId UNIQUE([Id]);--Id sütununun unikal təyin edilməsi
    GO
```  

indi aşağıdakı kodları icra etsək 'Ofis Ləvazimatları' adlı kateqoriya əlavə olunacaq lakin 'Məişət Əşyaları' kateqoriyasını yükləyərkən unikallığın pozulmasının şahidi olacayıq.Çünki hər ikisinin Id dəyəri 1-dir.'Məişət Əşyaları'-na aid olan Id dəyərini 2 ilə əvəz etsək normal qaydada icra olunacaq.

```
    use [Intelect];
    go
    insert into [Category]([Id],[Name]) values(1,N'Ofis Ləvazimatları');
    insert into [Category]([Id],[Name]) values(1,N'Məişət Əşyaları');
    go
```  

<h2 id="primarykey">Əsas açar (Primary Key)</h2>

**Primary Key** - yəni əsas acar məlumatı təyin edən açardır adından da göründüyü kimi.Və bir öncəki nümunə ilə müqayisə etdikdə birbirinə çox bənzəsə də lakin Primary Key-in təyinatı tam fərqlidir.Yəni hər cədvəldə ən azından bir əsas açar olmalıdır.Əsas açar həm təkrarlanmaların qarşısını alır həm də həmin sahəyə null dəyər daxil olmasının qarşısını alır.Yəni fərqli yanaşsaq "NOT NULL" və "UNIQUE" məhdudlaşdırıcılarını eyni anda əvəz edir.Bir cədvəldə ancaq bir ədəd "Primary Key " təyin etmək olar.Əvvəl yaratdığımız "UCategoryId" **UNIQUE** məhdudlaşdırıcını silib **Primary Key** məhdudlaşdırıcısını əlavə edirik.

```
    use [Intelect];
    go
    -- ilk öncə unikallıq məhdudlaşdırıcısını ləğv edirik
    ALTER TABLE [Category]
    DROP CONSTRAINT  UCategoryId;
    --sonra Id dəyərinin null olmasının qarşısını alırıq
    ALTER TABLE [Category]
    ALTER COLUMN Id int not null;
    --sonda isə əsas açar təyin edirik Category cədvəlimiz üçün.
    ALTER TABLE [Category]
    ADD CONSTRAINT  PK_Category PRIMARY KEY([Id]);
    go
```  


Və ya cədvəli əvvəlcədən bu keçilənləri əsas tutaraq belə yarada bilərdik.

```
    use [Intelect];
    GO
    CREATE TABLE Category(
    [Id] int NOT NULL PRIMARY KEY,
    [Name] nvarchar(150) NOT NULL,
    [CreatedDate] date NOT NULL DEFAULT GETDATE()
    )
    GO
```

<h2 id="check">Şərt məhdudlaşdırıcısı (Check Constraints)</h2>

Bu məhdudlaşdırıcı növü daxil edilən məlumatların dəyərlərinin məhdudlaşdırılması üçün istifadə edilir.Yəni əgər biz telefon nömrəsi üçün 13 simvol daxil edilməsini istəyiriksə <b>Check Constraint</b>lərdən istifadə edə bilərik.Və ya e-mail adres ya ip adrres kimi məlumatların daxil edilməsi üçün xüsusi Regular Expression təyin edib məhdudiyyət yarada bilərik.Deyəkki Users cədvəli yaradırıq və <b>LEN</b> funksiyasından istifadə edərək daxil edilən <b>Phone</b> dəyərinin 13 simvoldan az olmasını məhdudlaşdırırıq.

```html
    use [Intelect];
    GO
    CREATE TABLE [User](
    [Id] int NOT NULL PRIMARY KEY IDENTITY,
    [Name] nvarchar(150) NOT NULL,
    [Email] varchar(100) not null,
    [Phone] char(13) not null CHECK (LEN([Phone]) = 13),
    [CreatedDate] date NOT NULL default getdate()
    )
    GO
```

indi isə yoxlamaq məqsədi ilə aşağıdakı kodu icra etsəniz xəta ilə qarılaşacağınızı təyin etdiyimiz məhdudlaşdırıcının işə düşdüyünü görəcəksiniz

```html
    use [Intelect];
    GO
    insert into [User]([Name],[Email],[Phone])
    values(N'Test','test@mail.ru','0551234567');
    GO
```

Əgər cədvəli yaradarkən bu məhdudlaşdırıcını təyin etməmişiksə onda aşağıdakı kodla bu məhdudiyyəti icra edə bilərik.


```html
    use [Intelect];
    GO
    ALTER TABLE [User]
    ADD CONSTRAINT CK_Phone CHECK (LEN([Phone]) = 13);
    GO
```


<h2 id="foreignkey">Xarici açar məhdudlaşdırıcısı (Foreign Key Constraints)</h2>
Bəzən bir obyekt haqqında bütün məlumatların bir cədvəəlin eyni sətrində saxlanılması təkrarların artması və məlumatın idarə olunmasını çətinləşdirir.Bir sözlə relyasiyasız verilənlərin yaranmasına gətirib çıxarır.Bu zaman məlumatın nizamlı şəkildə bölünməsi lazım olur və bunun idarə edilməsi məlumat bütövlüyünün qorunması üçün  "Foreign Key Constraints"lərdən istifadə edirik.Misal üçün istifadəçinin rolunu təyin etmək üçün "Role" cədvəli yaradıb mövcud rolları o cədvəldə saxlayacağıq.Sonra isə "User" cədvəlinə "RoleId" sütunu əlavə edib əlaqələndirəcəyik.Aşağıdakı komandaları ardıcıllıqla izləmək lazımdır.

```html
    use [Intelect];
    GO
    --role cədvəli yaradırıq
    CREATE TABLE [Role](
    [Id] int NOT NULL PRIMARY KEY IDENTITY,
    [Name] nvarchar(150) NOT NULL,
    [CreatedDate] date NOT NULL default getdate()
    )

	--user rolunu əlavə edirik
	insert into [Role]([Name])values(N'User');

	--istifadəçilər cədvəlinə rol kodu sütunu əlavə edirik
	ALTER TABLE [User]
	ADD [RoleId] int default 1;

	--İstifadəçilər cədvəlinin Role cədvəli ilə əlaqəsinin yoxlanılması üçün xarici açar məhdudlaçdırıcısından istifadə edirik.
	ALTER TABLE [User]
	ADD FOREIGN KEY (RoleId) REFERENCES [Role](Id);
    GO
```

yəni əgər **RoleId** sütununa **Role** cədvəlində olmayan bir **Id** dəyəri verərsək əgər, məlumat bütövluyünün qorunmadığından komanda icra olunmayacaq

```html
    use [Intelect];
    GO
    insert into [User]([Name],[Email],[Phone],[RoleId])
    values(N'Test-2','test2@mail.ru','055-123-45-76',2);
    GO
```