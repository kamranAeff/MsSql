# Qoşma operatorları

İndiyə qədər istifadə etdiyimiz cədvələ baxarsaq "Qrup Adı" sütununda təkrarlanmalar olduğunu görürük.Təsəvvür edin ki qrupun adı dəyişilir bu zaman 4 sətirdə dəyikiklik etmək nə dərəcədə doğrudur?Düşündükcə həqiqətən də görürükki bu halda biz vaxt itirə bilərik,bundan savayı səhv etmə ehtimalımız yüksək olacaqdır.

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
Nəticəyə baxaq

<table>
<thead>
<tr>	
<th>Id</th>
<th>Name</th>
<th>Description</th>
<th>CategoryId</th>
<th>CreatedDate</th>
</tr>
</thead>
<tbody>
<tr><td>1</td><td>Wonlex GW100 Pink</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>2</td><td>Wonlex Q50 Charisma BLACK</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>3</td><td>Samsung Galaxy S10 Dual (SM-G973) White</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>4</td><td>Xiaomi Mi A3 4/128GB White</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>5</td><td>Blackview BV1000 yellow</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>6</td><td>Huawei Y9 2019 4/64GB Red</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>7</td><td>FLY TS114 BLACK</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>8</td><td>Blackview BV5500 Pro yellow</td><td></td><td>4</td><td>2019-09-15</td></tr>
<tr><td>9</td><td>Lenovo TB 7104I/3G -Wi-Fi/7 BLACK</td><td></td><td>3</td><td>2019-09-15</td></tr>
<tr><td>10</td><td>Samsung Galaxy Tab A 8.0 (SM-T295) Black</td><td></td><td>3</td><td>2019-09-15</td></tr>
<tr><td>11</td><td>Lenovo TAB E10 TB-X104F/10.1 BLACK</td><td></td><td>3</td><td>2019-09-15</td></tr>
<tr><td>12</td><td>Lenovo TAB 4 10 LTE (TB-X304L) black</td><td></td><td>3</td><td>2019-09-15</td></tr>
<tr><td>13</td><td>Samsung Galaxy Tab A (SM-T385) GOLD</td><td></td><td>3</td><td>2019-09-15</td></tr>
<tr><td>14</td><td>Huawei M5 Lite 3+32 Space Grey</td><td></td><td>3</td><td>2019-09-15</td></tr>
<tr><td>15</td><td>Apple MacBook Air 13″ MVFK2</td><td></td><td>2</td><td>2019-09-15</td></tr>
<tr><td>16</td><td>Apple MacBook Air 13″ MVFH2</td><td></td><td>2</td><td>2019-09-15</td></tr>
<tr><td>17</td><td>Monoblok HP ENVY 27-B170ur i7/16/nv4/1tb128/win10</td><td></td><td>2</td><td>2019-09-15</td></tr>
<tr><td>18</td><td>Noutbuk Asus Tuf Gaming FX505DD BQ121 </td><td></td><td>2</td><td>2019-09-15</td></tr>
<tr><td>19</td><td>Noutbuk Acer Predator Helios 300 PH315-52-718G </td><td></td><td>2</td><td>2019-09-15</td></tr>
<tr><td>20</td><td>Musiqi merkezi SONY MHC-V82D</td><td></td><td>1</td><td>2019-09-15</td></tr>
<tr><td>21</td><td>Speaker Sony SRS-XB21 Wireless</td><td></td><td>1</td><td>2019-09-15</td></tr>
<tr><td>22</td><td>JBL Pulse 3 Black</td><td></td><td>1</td><td>2019-09-15</td></tr>
</tbody>
</table>

<table>
<thead>
<tr><th>Id</th><th>Name</th><th>CreatedDate</th></tr>
</thead>
<tbody>
<tr><td>1</td><td>Audio,video</td><td>2019-09-15</td></tr>
<tr><td>2</td><td>Kompüter və ofis avadanlığı</td><td>2019-09-15</td></tr>
<tr><td>3</td><td>Planşetlər</td><td>2019-09-15</td></tr>
<tr><td>4</td><td>Telefonlar, Saatlar və Nömrələr</td><td>2019-09-15</td></tr>
</tbody>
</table>


Bəli sizinlə tam razıyam.Məhsul cədvəlinə baxıb CategoryId-yə nəzarən aşağıdakı cədvəllə uyğunlaşdırıb hansı kateqoriyaya aid olduğunu düşünürsüz?
Əlbəttə gəl indi bunu EndUser-ə(istifadəçiyə) başa sal?!?!?!?!
Bəli istifadəçiyə başa sala bilmərik,çünki sən hələ bundan sonrakı hissələri oxumamısan :)


Bu tipli məsələlərin həlli üçün ən çox istifadə olunan 4 birləşdirmə operatorları var ki, bunlarla 2 və daha artıq cədvəli bir birinə bağlayırıq.
<br/><br/><br/>
<h2 id="innerjoin">Inner join</h2>
<strong>Inner Join</strong> - operatoru özündən sağdakı və soldakı cədvəli uyğun sütunlara görə birləşdirərək tam uyğun gələn məlumatlara görə birləşməni icra edir.
İndi biz <strong>Products(<em>CategoryId</em>)</strong> və <strong>Category(<em>Id</em>)</strong> cədvəlini birləşdirək və məhsullar üzrə məlumatı tam təsvir edək.

 ```html
    USE [Intelect]
    GO  
    select 
	p.Id 
	,p.Name
	,p.Description
	,p.CategoryId
	,c.Name [CategoryName]
	,p.CreatedDate 
    from [dbo].[Products] p
	inner join [dbo].[Category] c on p.CategoryId=c.Id;
    GO
```

<table>
<thead>
<tr>	
<th>Id</th>
<th>Name</th>
<th>Description</th>
<th>CategoryId</th>
<th>CategoryName</th>
<th>CreatedDate</th>
</tr>
</thead>
<tbody><tr><td>1</td><td>Wonlex GW100 Pink</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>2</td><td>Wonlex Q50 Charisma BLACK</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>3</td><td>Samsung Galaxy S10 Dual (SM-G973) White</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>4</td><td>Xiaomi Mi A3 4/128GB White</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>5</td><td>Blackview BV1000 yellow</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>6</td><td>Huawei Y9 2019 4/64GB Red</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>7</td><td>FLY TS114 BLACK</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>8</td><td>Blackview BV5500 Pro yellow</td><td></td><td>4</td><th>Telefonlar, Saatlar və Nömrələr</th><td>2019-09-15</td></tr>
<tr><td>9</td><td>Lenovo TB 7104I/3G -Wi-Fi/7 BLACK</td><td></td><td>3</td><th>Planşetlər</th><td>2019-09-15</td></tr>
<tr><td>10</td><td>Samsung Galaxy Tab A 8.0 (SM-T295) Black</td><td></td><td>3</td><th>Planşetlər</th><td>2019-09-15</td></tr>
<tr><td>11</td><td>Lenovo TAB E10 TB-X104F/10.1 BLACK</td><td></td><td>3</td><th>Planşetlər</th><td>2019-09-15</td></tr>
<tr><td>12</td><td>Lenovo TAB 4 10 LTE (TB-X304L) black</td><td></td><td>3</td><th>Planşetlər</th><td>2019-09-15</td></tr>
<tr><td>13</td><td>Samsung Galaxy Tab A (SM-T385) GOLD</td><td></td><td>3</td><th>Planşetlər</th><td>2019-09-15</td></tr>
<tr><td>14</td><td>Huawei M5 Lite 3+32 Space Grey</td><td></td><td>3</td><th>Planşetlər</th><td>2019-09-15</td></tr>
<tr><td>15</td><td>Apple MacBook Air 13″ MVFK2</td><td></td><td>2</td><th>Kompüter və ofis avadanlığı</th><td>2019-09-15</td></tr>
<tr><td>16</td><td>Apple MacBook Air 13″ MVFH2</td><td></td><td>2</td><th>Kompüter və ofis avadanlığı</th><td>2019-09-15</td></tr>
<tr><td>17</td><td>Monoblok HP ENVY 27-B170ur i7/16/nv4/1tb128/win10</td><td></td><td>2</td><th>Kompüter və ofis avadanlığı</th><td>2019-09-15</td></tr>
<tr><td>18</td><td>Noutbuk Asus Tuf Gaming FX505DD BQ121 </td><td></td><td>2</td><th>Kompüter və ofis avadanlığı</th><td>2019-09-15</td></tr>
<tr><td>19</td><td>Noutbuk Acer Predator Helios 300 PH315-52-718G </td><td></td><td>2</td><th>Kompüter və ofis avadanlığı</th><td>2019-09-15</td></tr>
<tr><td>20</td><td>Musiqi merkezi SONY MHC-V82D</td><td></td><td>1</td><th>Audio,video</th><td>2019-09-15</td></tr>
<tr><td>21</td><td>Speaker Sony SRS-XB21 Wireless</td><td></td><td>1</td><th>Audio,video</th><td>2019-09-15</td></tr>
<tr><td>22</td><td>JBL Pulse 3 Black</td><td></td><td>1</td><th>Audio,video</th><td>2019-09-15</td></tr>
</tbody>
</table>

Gördüyümüz kimi,<strong>Inner Join</strong> - iki cədvəli birləşdirərək tam nəticə almağımıza təminat verdi.

<br/><br/><br/>
<h2 id="leftjoin">Left join</h2>
<strong>Left Join</strong> - operatoru özündən sağdakı və soldakı cədvəli uyğun sütunlara görə <strong>sol tərəfdəki cədvəli əsas tutaraq</strong> birləşdirir, sol tərəfdəki bütün məlumatları götürüb sağ tərəfdəki məlumatlardan uyğun gələnlə birləşdirib,uyğun gəlməyənləri boş buraxır.
İndiki halda yuxarıdakı sorğudakı <strong>Inner Join</strong>-i,<strong>Left Join</strong>-lə əvəz etsək heç bir dayişiklik olmayacaq.Fərqi görmək üçün bəzi sehirli toxunuşlara ehtiyyacımız var.

[CategoryId] sütununun həmcinin boş buraxıla bilməsi üçün aşaıdakı komanda ilə cədvəlin sxemasını dəyişirik.

 ```html
    USE [Intelect]
    GO  
    ALTER TABLE [dbo].[Products]
    ALTER COLUMN CategoryId int NULL;
    GO
```
sonra isə yeni məhsul əlavə edirik amma <strong>CategoryId</strong> sütununu boş buraxacayıq.

 ```html
    USE [Intelect]
    GO  
    INSERT [dbo].[Products] ([Name], [CategoryId], [CreatedDate]) 
    VALUES (N'Fotoaparat Canon EOS M100 15-45mm IS STM Kit Black', NULL, '2019-09-15');
    GO
```

sonra isə yuxarıdakı <strong>inner join</strong> ilə yazdığımız sorğunu <strong>left join</strong>-lə əvəzləyib nəticəyə baxaq.

 ```html
    USE [Intelect]
    GO  
    SELECT
    p.*,
    c.*
    from [dbo].[Products] p
    left join [dbo].[Category] c on p.CategoryId=c.Id;
    GO
```
<table>
<thead>
<tr>	
<th>Id</th>
<th>Name</th>
<th>Description</th>
<th>CategoryId</th>
<th>CreatedDate</th>
<th>Id</th>
<th>Name</th>
<th>CreatedDate</th>
</tr>
</thead>
<tbody><tr>	
<td>1</td>
<td>Wonlex GW100 Pink</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>2</td>
<td>Wonlex Q50 Charisma BLACK</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>3</td>
<td>Samsung Galaxy S10 Dual (SM-G973) White</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>4</td>
<td>Xiaomi Mi A3 4/128GB White</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>5</td>
<td>Blackview BV1000 yellow</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>6</td>
<td>Huawei Y9 2019 4/64GB Red</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>7</td>
<td>FLY TS114 BLACK</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>8</td>
<td>Blackview BV5500 Pro yellow</td>
<td><em>NULL</em></td>
<th>4</th>
<td>2019-09-15</td>
<td>4</td>
<td>Telefonlar, Saatlar və Nömrələr</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>9</td>
<td>Lenovo TB 7104I/3G -Wi-Fi/7 BLACK</td>
<td><em>NULL</em></td>
<th>3</th>
<td>2019-09-15</td>
<td>3</td>
<td>Planşetlər</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>10</td>
<td>Samsung Galaxy Tab A 8.0 (SM-T295) Black</td>
<td><em>NULL</em></td>
<th>3</th>
<td>2019-09-15</td>
<td>3</td>
<td>Planşetlər</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>11</td>
<td>Lenovo TAB E10 TB-X104F/10.1 BLACK</td>
<td><em>NULL</em></td>
<th>3</th>
<td>2019-09-15</td>
<td>3</td>
<td>Planşetlər</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>12</td>
<td>Lenovo TAB 4 10 LTE (TB-X304L) black</td>
<td><em>NULL</em></td>
<th>3</th>
<td>2019-09-15</td>
<td>3</td>
<td>Planşetlər</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>13</td>
<td>Samsung Galaxy Tab A (SM-T385) GOLD</td>
<td><em>NULL</em></td>
<th>3</th>
<td>2019-09-15</td>
<td>3</td>
<td>Planşetlər</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>14</td>
<td>Huawei M5 Lite 3+32 Space Grey</td>
<td><em>NULL</em></td>
<th>3</th>
<td>2019-09-15</td>
<td>3</td>
<td>Planşetlər</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>15</td>
<td>Apple MacBook Air 13″ MVFK2</td>
<td><em>NULL</em></td>
<th>2</th>
<td>2019-09-15</td>
<td>2</td>
<td>Kompüter və ofis avadanlığı</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>16</td>
<td>Apple MacBook Air 13″ MVFH2</td>
<td><em>NULL</em></td>
<th>2</th>
<td>2019-09-15</td>
<td>2</td>
<td>Kompüter və ofis avadanlığı</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>17</td>
<td>Monoblok HP ENVY 27-B170ur i7/16/nv4/1tb128/win10</td>
<td><em>NULL</em></td>
<th>2</th>
<td>2019-09-15</td>
<td>2</td>
<td>Kompüter və ofis avadanlığı</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>18</td>
<td>Noutbuk Asus Tuf Gaming FX505DD BQ121 </td>
<td><em>NULL</em></td>
<th>2</th>
<td>2019-09-15</td>
<td>2</td>
<td>Kompüter və ofis avadanlığı</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>19</td>
<td>Noutbuk Acer Predator Helios 300 PH315-52-718G </td>
<td><em>NULL</em></td>
<th>2</th>
<td>2019-09-15</td>
<td>2</td>
<td>Kompüter və ofis avadanlığı</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>20</td>
<td>Musiqi merkezi SONY MHC-V82D</td>
<td><em>NULL</em></td>
<th>1</th>
<td>2019-09-15</td>
<td>1</td>
<td>Audio,video</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>21</td>
<td>Speaker Sony SRS-XB21 Wireless</td>
<td><em>NULL</em></td>
<th>1</th>
<td>2019-09-15</td>
<td>1</td>
<td>Audio,video</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>22</td>
<td>JBL Pulse 3 Black</td>
<td><em>NULL</em></td>
<th>1</th>
<td>2019-09-15</td>
<td>1</td>
<td>Audio,video</td>
<td>2019-09-15</td>
</tr>
<tr>	
<td>23</td>
<td>Fotoaparat Canon EOS M100 15-45mm IS STM Kit Black</td>
<td><em>NULL</em></td>
<th><em>NULL</em></th>
<td>2019-09-15</td>
<td><em>NULL</em></td>
<td><em>NULL</em></td>
<td><em>NULL</em></td>
</tr>
</tbody>
</table>

Nəticəyə baxdığınızda isə-23cü sətrdəki yeni məhsula görə he bir kateqoriyanın uyğun gəlmədiyinə görə <strong>Category</strong> cədvəlinə aid bütün sütunlara <em>NULL</em> mənimsədilib.Bu sorğunun nəticəsində 23 sətir gəldiyi halda,yenidən <strong>inner join</strong>-lə yoxlasanız 22 məlumat gələcək,23cü məhsul uyğun kateqoriya tapa bilmədiyi üçün nəticədə görünməyəcək.

<br/><br/><br/>
<h2 id="rightjoin">Right join</h2>
<strong>like</strong>
<br/><br/><br/>
<h2 id="fulljoin">Full join</h2>
<strong>like</strong>




