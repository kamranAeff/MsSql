# Seçim ifadələri

Öncəki dərslərlə biz yeni bir baza yaratmaq,bazada cədvəllər yatatmaq və yaratdığımız cədvəllərə məlumat əlavə etməyi, redaktə etmək və silməyi öyrənmişdik.Bu dərsimizdə isə biz cədvəlimizdəki məlumatların axtarılması axtardığımız məlumatların tapılması,axtarma fəndlərini öyrənəcəyik.Axtarış etmək və xüsusi seçim şərtləri ilə məlumatları seçməyimiz üçün bizim əlimizdə ilk öncə ən az 20-30 məlumatı özündə saxlayan məlumat toplusu-**Cədvəl** olmalıdır.Bunun üçün ilk öncə tələbə cədvəlimizi yaradaq və həmçinin keçdiklərimizi xatırlayaq.

İlk öncə cədvəlimizi yaradaq.Bu nümunəmizdə tələbə cədvəlimiz aşağıdakı sütunlardan (columns) ibarət olacaqdır:
- Tələbənin adı
- Tələbənin soyadı
- Doğum tarixi
- Cinsi
- Doğum yeri
- İxtisası
- Qrupu
> və birdə hər cədvəldə olması mütləq şəkildə lazım olan <strong>sıra nömrəsi(Id)</strong>sütunundan.

İndi isə gəlin uyğun tiplərin seçilməsi üçün qərar qəbul edək.

<dl>
  <dt>Id</dt>
  <dd>İlk öncə <strong>sıra nömrəsi-Id</strong> sütunu üçün hansı tip lazımdı onu seçək.İlk öncə bilirikki sıra nömrəsi rəqəm tipli məlumatdır.Ona görə də <a href="datatypes.md#numerictypes">rəqəm tipləri</a> arasından uyğununu seçirik.Uyğun tipi seçmək üçün ilk öncə saxlayacağımız məlumat tipini təyin edirik.Sonra isə məlumatın həcmini.
Tələbə sistemində milyonlarda tələbə ola bilər bu o deməkdirki milyonları aşacaq bizim <strong>Id</strong> sütununda saxlayacağımız məlumat.Bu zaman  <a href="datatypes.md">Verilənlərin tipləri</a> bölümünü birdə gözdən keçirməyimiz məsləhətdir.Seçimimizi sonradan dəyişə bilərik ama əvvəlcədən mümkün ehtimalları nəzərə almağımız məsləhətdir.Beləliklə bu qərara gəlirikki bizim <strong>sıra nömrəsi-Id</strong> sütununun tipinin <strong>int</strong> olması daha məsləhətlidir.</dd>
  
  <dt>Name</dt>
  <dd>Bu dəfə isə <strong>Tələbənin adı-Name</strong> sütunu üçün hansı tip lazımdı onu seçək.İlk öncə bilirikki tələbənin adı mətn tipli məlumatdır.Ona görə də <a href="datatypes.md#stringtypes">mətn tipləri</a> arasından uyğununu seçirik.Uyğun tipi seçmək üçün ilk öncə saxlayacağımız məlumat tipini təyin edirik.Sonra isə məlumatın həcmini.Tələbənin adı mətn tiplidir və real həyatda insan adları 10-15 simvolu keçməyən hərf yığımından ibarətdir.Eyni zamanda adlar Ə,Ş kimi unicode simvolları da özündə saxlaya bilər.Bu zaman <a href="datatypes.md">Verilənlərin tipləri</a> bölümünü birdə gözdən keçirməyimiz məsləhətdir.Beləliklə bu qərara gəlirikki bizim <strong>Tələbənin adı-Name</strong> sütununun tipinin <strong>nvarchar(15)</strong> olması daha məsləhətlidir.</dd> 

  <dt>Surname</dt>
  <dd><strong>Tələbənin soyadı-Surname</strong> sütunu üçün hansı tip lazımdı onu seçək.Bu yəni soyad göstəricisinin tipi və həcmi ad göstəricisi ilə eynilik təşkil etdiyinə görə yuxarıdakı Ad üçün aldığımız qərar soyada da şamil olunur.</dd>

  <dt>BirthDate</dt>
  <dd>Bu dəfə isə <strong>Tələbənin Doğum tarixi-BirthDate</strong> sütunu üçün hansı tip lazımdı onu seçək.İlk öncə bilirikki tələbənin doğum tarixi tarix tipli məlumatdır.Ona görə də <a href="datatypes.md#dateandtimetypes">tarix və zaman tipləri</a> arasından uyğununu seçirik.Uyğun tipi seçmək üçün ilk öncə saxlayacağımız məlumat tipini təyin edirik.Sonra isə məlumatın həcmini.Tələbənin doğum tarixi <i>tarix tiplidir</i>.Beləliklə bu qərara gəlirikki bizim <strong>Tələbənin Doğum tarixi-BirthDate</strong> sütununun tipinin <strong>Date</strong> olması daha məsləhətlidir.</dd>

  <dt>Gender</dt>
  <dd><strong>Tələbənin cinsi-Gender</strong> sütunu üçün hansı tip lazımdı onu seçək.Bu yəni tələbənin cinsi göstəricisinin tipi və həcmi ad göstəricisi ilə eynilik təşkil etdiyinə görə yuxarıdakı Ad üçün aldığımız qərar soyada da şamil olunur.Lakin "Kişi" və "Qadın" deyə iki cins qeyd edəcəyimizi nəzərə alsaq görərikki məlumatın həcmi maximim 5 simvol ola bilər.Bu zaman <strong>nvarchar(5)</strong> tipi seçirik bu sütun üçün.</dd>

  <dt>BirthPlace</dt>
  <dd><strong>Doğum yeri-BirthPlace</strong> sütunu üçün hansı tip lazımdı onu seçək.Bu yəni tələbənin cinsi göstəricisinin tipi və həcmi ad göstəricisi ilə eynilik təşkil etdiyinə görə yuxarıdakı Ad üçün aldığımız qərar soyada da şamil olunur.Lakin doğum yeri xanasında şəhər,rayon,qəsəbə,küçə mənzil qeyd edəcəyimizi nəzərə alsaq görərikki məlumatın həcmi orta hesabla 100+ simvol ola biler.Bu zaman <strong>nvarchar(100)</strong> tipi seçirik bu sütun üçün.</dd>


  <dt>Profession</dt>
  <dd><strong>İxtisasi-Profession</strong> sütunu üçün hansı tip lazımdı onu seçək.Cavabınızı eşidir kimiyəm.Bəli yenə mətn tipli məlumatdir.100-150 simvolluq həcmə malik olacaq.Ümumiyyətlə nvarchar tipi variable-Length(yəni yazılmış məlumatın uzunluğu qədər yer tutur) olduğu üçün max uzunluğun çox götürsək fövqaladə problem yaratmış olmarıq.Beləliklə sütunun tipini <strong>nvarchar(150)</strong> seçirik.</dd>


  <dt>Group</dt>
  <dd>Son olaraq <strong>Qrupu-Group</strong> sütunu üçün hansı tip lazımdı onu seçək.Mətn tipli olduğu üçün və "A0000" kimi məlumat saxlayacaöğımızı nəzərə alaraq mətn tipli sahə ayıracağımızı bilirik və həcmi 5 simvol kimi qəbul edirik.Beləliklə sütunun tipini <strong>varchar(5)</strong> seçirik,ona görə ki, unicode simvollara ehtiyyac olmur bu sahə-Group üzrə.</dd>
</dl>

İndi isə aldığımız qərarlara əsasən yeni cədvəl yaradaq.

```html
    use [Intelect];
    go
    CREATE TABLE Students(
        [Id] int not null identity , -- Əsas açar(Primary Key),avtomatik artan(identity) ve boş buraxlılmayan bir sütun təyin etdik
        [Name] nvarchar(15) not null,
    	[Surname] nvarchar(15) not null,
    	[BirthDate] date not null,
    	[Gender] nvarchar(5) not null,
    	[BirthPlace] nvarchar(100) not null,
    	[Group] varchar(5) not null
    );
    go
```

Və yeni yaratdığımız üçün cədvəl hazırda boşdur.İndi isə sorğulamağı öyrənməyimiz üçün ilk öncə cədvələ test məlumatlar dolduraq.

```html
    USE [Intelect]
    GO

    INSERT INTO [dbo].[Students]([Name],[Surname],[BirthDate],[Gender],[BirthPlace],[Group])
    VALUES(N'Adil',N'Abbasov','1990-01-02',N'Kişi',N'Azərbaycan,Bakı. Nəsimi. B1.M8',N'A0001'),
    (N'Sənan',N'İsgəndərov','1995-05-23',N'Kişi',N'Azərbaycan,Bakı. Nizami. B2.M2',N'A0001'),
    (N'Qəmbər',N'Kazımov','1998-01-13',N'Kişi',N'Azərbaycan,Abşeron. Xırdalan. M18',N'A0001'),
    (N'Zülfiyyə',N'Əliyeva','1995-01-02',N'Qadın',N'Azərbaycan,Bakı. Nəsimi. B1.M8',N'A0001'),
    (N'Zeynəb',N'Zamanlı','1993-11-02',N'Qadın',N'Azərbaycan,Gəncə. Kəpəz. B1.M8',N'A0002'),
    (N'Əli',N'Cavadov','1990-10-02',N'Kişi',N'Azərbaycan,Şəki. E218',N'A0002'),
    (N'Qalib',N'Kərimli','1990-09-06',N'Kişi',N'Azərbaycan,Sumqayıt. E120',N'A0002');
    GO
```

Beləliklə artıq cədvəlimizdə 7 tələbə var.Baxmaq üçün

```html
    USE [Intelect]
    GO

    select * from [dbo].[Students];
    GO
```

Komandasını icra edə bilərsiz.


<h2 id="search1">Məlumatların şərtlərə görə seçilməsi</h2>
Real həyatda bəzən milyonlarca məlumatla qarşılaşırıq və bu məlumatların icindən sadecə xüsusi şərtləri ödəyən məlumatları əldə etmə zərurəti ilə qarş-qarşıya qalırıq.Və bu zaman artıq biz xüsusi şərtlər tətbiq edərək məlumat seçməyə başlayırıq.

Bunun üçün ilk öncə <strong>where</strong>-açar sözüçü istifadə edirik.Yəni bu açar söz vasitəsi ilə artıq bu məlumat toplusunu xüsusi şərtə tabe tutaraq sorğulayırıq.
Deyək ki, <strong>A0001</strong> grupunda oxuyan tələbələrin siyahısına baxmaq istəyirik.Bu zaman sadə select sorğumuza aşağıdakı kimi şərt əlavə edirik.

```html
    USE [Intelect]
    GO
    select * from [dbo].[Students] where [Group]='A0001';
    GO
```

Beləliklə artıq ümumilikdə 7 məlumat olan cədvəldən xüsusi şərtə uyğun 4 məlumatı tapdıq.İndi isə şərti biraz da artıraraq nəticəni biraz da azaldaq.Misal üçün deyək ki,
Tələbələr cədvəlindən bizə <q><strong>A0001</strong>-qrupunda oxuyan bütün kişi tələbələrin siyahısı</q> lazımdır.Bu siyahını əldə etmək üçün lazımlı sorğunu tərtib edək:

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students] 
    where [Group]='A0001' and [Gender]=N'Kişi';
    GO
```

Diqqət etsəniz görəcəksiniz ki,<strong>[Gender]=N'Kişi'</strong> şərtini əlavə etmişik və iki şərti birləşdirmək üçün <strong>and</strong> şərt birləşdiricisindən istifadə edirik.

İndi isə bizə <q><strong>A0001</strong>-qrupunda oxuyan bütün kişi tələbələrin siyahısı və həmçinin <strong>A0002</strong>-qrupunda oxuyan tələbələrin siyahisi ilə birlikdə</q> lazımdır.Bu siyahını əldə etmək üçün lazımlı sorğunu tərtib edək:

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students] 
    where [Group]='A0001'and [Gender]=N'Kişi' or [Group]='A0002';
    GO
```

Diqqət etsəniz görəcəksiniz ki,  <strong>[Group]='A0002'</strong> şərtini əlavə etmişik və üçüncü şərti birləşdirmək üçün <strong>or</strong> şərt birləşdiricisindən istifadə edirik.

Bəzən isə biz məlumatın hamisini yox, bir hissəsini xatırlaya bilirik və məlumatın xatırladığımız hissəsinə görə axtarış etmək məcburiyyətində qalırıq.Deyəkki doğum yeri nizami rayonu olan bütün tələbələri axtarmağımız lazım gəlir, yəni <q>DoğumYeri xanasında Nizami rayonu qeyd olunan tələbələri axtarırıq</q>.Bu zaman sorğunu aşağıdakı kimi tərtib edirik.

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students] 
	where [BirthPlace] like N'%nəsimi%';
    GO
```

Yəni mətn tipli məlumatları sorğulayarkən <strong>bərabərdir(=)</strong> işarətindən savayı <strong>like</strong> operatorundan da istifadə edilir ki,bu operator vasitəsi ilə,axtardığımız sözlə başlayan,axtardığımız sözlə bitən və yaxut da içində axtardığımız söz olan məlumatların tapılması üçün istifadə edirik.

Deyəkki "Surname-Soyad" sütunu üzrə axtarış edərkən
1. "Ab" - ilə başlayan soyada malik(Abdullayev,Abbasov,və s.) tələbələri seçmək istəyirik,bu zaman şərti aşağıdakı kimi yazmalıyıq:
> ... [Surname] like N'Ab%'
2. "zadə" - ilə bitən soyada malik(Abdullazadə,Əlizadə,və s.) tələbələri seçmək istəyirik,bu zaman şərti aşağıdakı kimi yazmalıyıq:
> ... [Surname] like N'%zadə'
3. ya da daxilində "man" - hissəciyi olan soyada malik(Zamanlı,Süleymanlı,və s.) tələbələri seçmək istəyirik,bu zaman şərti aşağıdakı kimi yazmalıyıq:
> ... [Surname] like N'%man%'





<h2 id="distinct">Təkrarsız məlumatların seçilməsi</h2>

Deyəkki belə bir sualla qarşılaşdıq.
Hansı fərqli qrup adı qeyd olunmuşdur tələbə cədvəlində?

İlk öncə yalnız Group sütununu görmək üçün sorğumuzu yeniləyək.

```html
    USE [Intelect]
    GO  
    select [Group] from [dbo].[Students];
    GO
```

Nəticəyə baxsaq 7 sətir görəcəyik.Lakin 2 fərqli məlumatdan ibarətdir.Belə hallarda məlumatların təkrarlanmasının qarşısını almaq lazımdır.Bunun üçün <strong>distinct</strong>  açar sözündən istifadə edirik.Aşağıdakı sorğu kodunu icra edərək problemimizin aradan qalxdığını görəcəyik.

```html
    USE [Intelect]
    GO  
    select distinct [Group] from [dbo].[Students];
    GO
```



<h2 id="order">Məlumatların fərqli göstəricilərinə görə sıralanması</h2>

Select operatoru ilə ən çox istifadə edilən operatorlardan biuri də <strong>order by</strong>operatorudur.Bu operator vasitəsi ilə select ifadəsinin nəticəsi göstərilmədən öncə qeyd olunmuş sütun və ya sütunlara görə sıralanıb istifadəçiyə göstərilir.
Misal üçün doğum tarixinin kiçikdən böyüyə sıralanması üzrə məlumatların göstərilməsi:

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students]
    order by [BirthDate] asc;  --asc yazılmaya da bilər,çünki susmaya görə asc qəbul edilir.
    GO
```

Və ya tam əksinə,doğum tarixinin böyükdən kiçiyə sıralanması üzrə məlumatların göstərilməsi:

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students]
    order by [BirthDate] desc;
    GO
```

Həmçinin bir neçə sütuna görə birdən, məlumatları sıralaya bilərik.Bunun üçün order by-dan sonra yazılan sütun adları vergüllə ayırılır.Misal üçün bütün tələbələri əvvəlcə qrupa və qrup daxilində isə çoxyaşlıdan azyaşlıya doğru düzürük

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students]
    order by [Group],[BirthDate];
    GO
```

Order By operatoru ilə məlumatları kiçikdən böyüyə,böyükdən kiçiyə sıralaya bildik.Lakin bəzən elə hallar olurki bizə fərqli ehtimallı məlumatları əldə edək.Misal üçün test sistemi yazaçayıqsa əgər,məcburuq ki sualların ardıcıllığı random olaraq fərqli ehtimalla gəlsin.Bu zaman biz select sorğusunu aşağıdakı kimi yazmalıyıq:  

```html
    USE [Intelect]
    GO  
    select * from [dbo].[Students]
    order by newid();
    GO
```

yəni <strong>order by</strong> operatorundan sonra sütun adı yox random funksiyası olan <strong>newid()</strong> ilə birgə istifadə edirik.



<h2 id="top">Limitli seçmə ifadələri</h2>
Xüsusən çox qeydin olduğu cədvəlləri sorğulayarkən sorğu müddəti çox vaxt ala bilir bəzən.Misal üçün bir bankın 10 milyon müştərisi olduğunu fikirləşin.Amma bizə bu müştərilərin 100 dənəsi lazımdır edəcəyimiz əməliyyat üçün.
Və ya yazdığımız sorğunun doğru tətbiq olunmasını yoxlayarkən  neticənin 20-30 dənəsinə nəzər yetirmək istəyərkən biz <strong>limitli seçmə ifadələri</strong>ni istifadə edirik.Bu əməliyyatı icra etmək üçün biz <strong>top([say])</strong> operatorundan istifadə edirik.Top operatorunu <strong>select</strong> operatorundan dərhal sonra yazırıq.

Test bazamızda yer alan 7 tələbənin ilk 3üç-ünü görmək istəyiriksə bu zaman,sorğunu aşağıdakı kimi yazmalıyıq.

```html
    USE [Intelect]
    GO  
    select top(3) * from [dbo].[Students];
    GO
```

Son üç tələbəni görmək istəyiriksə o zaman aşağıdakı kimi redaktə etməliyik sorğumuzu:

```html
    USE [Intelect]
    GO  
    select top(3) * from [dbo].[Students]
    order by id desc;
    GO
```

<dl>
<dt>Tapşırıq</dt>
    <dd>
        <strong>1.</strong> Ən cavan 5 tələbəni sıra ilə göstərmək.  <br/>
        <strong>2.</strong> Ən yaşlı 4 tələbəni sıra ilə göstərmək.  <br/>
        <strong>3.</strong> Ən gənc 3 xanım tələbənin siyahısını tərtib etmək.  <br/>
        <strong>4.</strong> Ən yaşlı 5 kişi tələbəni gəncdən yaşlıya doğru sıra ilə siyahı şəklində tərtib etmək.  <br/>
        <strong>5.</strong> Qrup üzrə 6 gənc tələbəni ən gəncdən ən yaşlıya doğru sıralayın.
    </dd>
</dl>

