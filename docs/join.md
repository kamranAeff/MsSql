# Qoşma operatorları

İndiyə qədər istifadə edəcəyimiz cədvələ baxarsaq "Qrup Adı" sütununda təkrarlanmalar olduğunu görürük.Təsəvvür edin ki qrupun adı dəyişilir bu zaman 4 sətirdə dəyikiklik etmək nə dərəcədə doğrudur?Düşündükcə həqiqətən də görürükki bu halda biz vaxt itirə bilərik,bundan savayı səhv etmə ehtimalımız yüksək olacaqdır.

Yaxudda bu tipli bir Məhsul cədvəlimiz var düşünün.Məhsul cədvəlində məhsul haqqında məlumatlar və birdə məhsul kateqoriyası olduğunu düşünün.Məhsulların hər biri üçün həmçinin kateqoriyalarının ingilis dilində tərcüməsi də tələb olunur.Bu zaman bizim 200-dən ibarət 5 çeşid(5 fərqli kategoriyaya aid) məhsulumuz var.Bu zaman hər kategoriyaya aid eyni sayda məhsul olduğunu düşünsək onda hər kateqoriyada 40 məhsul var.Bu o deməkdirki 1 kategoriyani ingilis dilinə çevirərkən eyni tərcüməni 40-sətrə yazmalıyam.Həlli nərdir bəs? Həlli Verilənlər bazasının normallaşdırılmasıdır.Nəzəri olaraq dediklərimizi praktiki olaraq icra edək.Məhsul cədvəlimizi yaradaq:


```html
    USE [Intelect]
    GO  
    create table dbo.Products(
	Id		int identity primary key, --acar sahesi
	[Name]	nvarchar(150) not null,
	[Description]	nvarchar(250) null,
	[CategoryName]  nvarchar(150) not null,
	[CreatedDate] [date] NOT NULL default getdate() --sisteme dusme tarixi
	)
    GO
```

İndi isə biraz məlumat edək praktiki izahlar üçün.Əvvəlcədən biliyimiz üsulla biraz məhsul əlavə edək cədvəlimizə.

```html
    USE [Intelect]
    GO  
    INSERT [dbo].[Products] ([Name], [Description], [CategoryName], [CreatedDate]) 
    VALUES (N'Wonlex GW100 Pink', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Wonlex Q50 Charisma BLACK', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Samsung Galaxy S10 Dual (SM-G973) White', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Xiaomi Mi A3 4/128GB White', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Blackview BV1000 yellow', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Huawei Y9 2019 4/64GB Red', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'FLY TS114 BLACK', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Blackview BV5500 Pro yellow', NULL, N'Telefonlar, Saatlar və Nömrələr', CAST(N'2019-09-15' AS Date))
    ,(N'Lenovo TB 7104I/3G -Wi-Fi/7 BLACK', NULL, N'Planşetlər', CAST(N'2019-09-15' AS Date))
    ,(N'Samsung Galaxy Tab A 8.0 (SM-T295) Black', NULL, N'Planşetlər', CAST(N'2019-09-15' AS Date))
    ,(N'Lenovo TAB E10 TB-X104F/10.1 BLACK', NULL, N'Planşetlər', CAST(N'2019-09-15' AS Date))
    ,(N'Lenovo TAB 4 10 LTE (TB-X304L) black', NULL, N'Planşetlər', CAST(N'2019-09-15' AS Date))
    ,(N'Samsung Galaxy Tab A (SM-T385) GOLD', NULL, N'Planşetlər', CAST(N'2019-09-15' AS Date))
    ,(N'Huawei M5 Lite 3+32 Space Grey', NULL, N'Planşetlər', CAST(N'2019-09-15' AS Date))
    ,(N'Apple MacBook Air 13″ MVFK2', NULL, N'Kompüter və ofis avadanlığı', CAST(N'2019-09-15' AS Date))
    ,(N'Apple MacBook Air 13″ MVFH2', NULL, N'Kompüter və ofis avadanlığı', CAST(N'2019-09-15' AS Date))
    ,(N'Monoblok HP ENVY 27-B170ur i7/16/nv4/1tb128/win10', NULL, N'Kompüter və ofis avadanlığı', CAST(N'2019-09-15' AS Date))
    ,(N'Noutbuk Asus Tuf Gaming FX505DD BQ121 ', NULL, N'Kompüter və ofis avadanlığı', CAST(N'2019-09-15' AS Date))
    ,(N'Noutbuk Acer Predator Helios 300 PH315-52-718G ', NULL, N'Kompüter və ofis avadanlığı', CAST(N'2019-09-15' AS Date))
    ,(N'Musiqi merkezi SONY MHC-V82D', NULL, N'Audio,video', CAST(N'2019-09-15' AS Date))
    ,(N'Speaker Sony SRS-XB21 Wireless', NULL, N'Audio,video', CAST(N'2019-09-15' AS Date))
    ,(N'JBL Pulse 3 Black', NULL, N'Audio,video', CAST(N'2019-09-15' AS Date));
    GO
```

indi isə cədvəlimizi yoxlayaq

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Products];
    GO
```

baxıb görürük ki,22 məlumat var.Və belə bişey lazımdı bizə.Kateqoriyaların ilgilis dilində tərcüməsi də lazımdı həmçinin.Bu halda <strong>[dbo].[Products]</strong> cədvəlimizə yeni bir sütun əlavə edib 22 dəfə eyni və fərqli tərcümələri əlavə edəcətik.


```html
    use [Intelect];
    go
    ALTER TABLE [dbo].[Products]
    ADD NameEn nvarchar(150);
    go
```

Tərcümələri doldurmağı sizə həvalə edirəm,problemi başa düşməyiniz üçün.Ama məncə artıq problemi anlamısınız sizdə.Bu problemi həll etmək üçün cədvəlimizi normallaşdırmalıyıq.Normallaşdırmaq dediyimiz təkrarlanan məlumatların başqa cədvəldə saxlanmasını təmin edərək məlumatların idarə edilməsini asanlaşdırıb bir mərkəzdən idarə edilməsini təmin edirik.İndi isə bunun üçün Kategoriya cədvəli yaradırıq və kategpriyaları təkrarsız cədvələ daxil edirik.

```html
    use [Intelect];
    go
	CREATE TABLE [dbo].[Category](
	[Id] int identity primary key,
	[Name] nvarchar(150) NOT NULL,
	[CreatedDate] datetime NOT NULL DEFAULT GETDATE())
	go

	insert into [dbo].[Category]([Name])
	values(N'Audio,video')
	,(N'Kompüter və ofis avadanlığı')
	,(N'Planşetlər')
	,(N'Telefonlar, Saatlar və Nömrələr');
	go
```

İndi isə Məhsul cədvəlimizi yenidən qurub normallaşdırmanı nəzərə alaq(yəni [CategoryName] sütununu uyğun olaraq  [CategoryId] ilə əvəz edib,[Category] cədvəlindən uyğun kodu [dbo].[Products] cədvəlinə əlavə edəcəyik). Aşağıdakı kodla məhsul cədvəlini silib yenidən yaradıb dolduracayıq.

```html
    USE [Intelect]
    GO  
    drop table dbo.Products    --mövcud cədvəli silirik
	GO  
    create table dbo.Products( --cədvəli yenidən normallaşdırılmış halda yaradırıq
	Id		int identity primary key, --acar sahesi
	[Name]	nvarchar(150) not null,
	[Description]	nvarchar(250) null,
	[CategoryId]  int not null,--yenilendi
	[CreatedDate] [date] NOT NULL default getdate() --sisteme dusme tarixi
	)
    GO
	INSERT [dbo].[Products] ([Name], [Description], [CategoryId], [CreatedDate]) 
    VALUES (N'Wonlex GW100 Pink', NULL, 4, '2019-09-15')
    ,(N'Wonlex Q50 Charisma BLACK', NULL, 4, '2019-09-15')
    ,(N'Samsung Galaxy S10 Dual (SM-G973) White', NULL, 4, '2019-09-15')
    ,(N'Xiaomi Mi A3 4/128GB White', NULL, 4, '2019-09-15')
    ,(N'Blackview BV1000 yellow', NULL, 4, '2019-09-15')
    ,(N'Huawei Y9 2019 4/64GB Red', NULL, 4, '2019-09-15')
    ,(N'FLY TS114 BLACK', NULL, 4, '2019-09-15')
    ,(N'Blackview BV5500 Pro yellow', NULL, 4, '2019-09-15')
    ,(N'Lenovo TB 7104I/3G -Wi-Fi/7 BLACK', NULL, 3, '2019-09-15')
    ,(N'Samsung Galaxy Tab A 8.0 (SM-T295) Black', NULL, 3, '2019-09-15')
    ,(N'Lenovo TAB E10 TB-X104F/10.1 BLACK', NULL, 3, '2019-09-15')
    ,(N'Lenovo TAB 4 10 LTE (TB-X304L) black', NULL, 3, '2019-09-15')
    ,(N'Samsung Galaxy Tab A (SM-T385) GOLD', NULL, 3, '2019-09-15')
    ,(N'Huawei M5 Lite 3+32 Space Grey', NULL, 3, '2019-09-15')
    ,(N'Apple MacBook Air 13″ MVFK2', NULL, 2, '2019-09-15')
    ,(N'Apple MacBook Air 13″ MVFH2', NULL, 2, '2019-09-15')
    ,(N'Monoblok HP ENVY 27-B170ur i7/16/nv4/1tb128/win10', NULL, 2, '2019-09-15')
    ,(N'Noutbuk Asus Tuf Gaming FX505DD BQ121 ', NULL, 2, '2019-09-15')
    ,(N'Noutbuk Acer Predator Helios 300 PH315-52-718G ', NULL, 2, '2019-09-15')
    ,(N'Musiqi merkezi SONY MHC-V82D', NULL, 1, '2019-09-15')
    ,(N'Speaker Sony SRS-XB21 Wireless', NULL, 1, '2019-09-15')
    ,(N'JBL Pulse 3 Black', NULL, 1, '2019-09-15');
    GO
```

Cədvəli yoxlayarkən məhsul cədvəlində kateqoriyanın adı yox kodu durduğunu görürük.Bu koda uyğun kateqoriyanı isə biz kateqoriyalar cədvəlindən tapa bilərik.

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Products]; --məhsullar
    select * from [dbo].[Category]; --kateqoriyalar
    GO
```



