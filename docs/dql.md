# Seçim ifadələri

Öncəki dərslərlə biz yeni bir baza yaratmaq,bazada cədvəllər yatatmaq və yaratdığımız cədvəllərə məlumat əlavə etməyi, redaktə etmək və silməyi öyrənmişdik.Bu dərsimizdə isə biz cədvəlimizdəki məlumatların axtarılması axtardığımız məlumatların tapılması,axtarma fəndlərini öyrənəcəyik.Axtarış etmək və xüsusi seçim şərtləri ilə məlumatları seçməyimiz üçün bizim əlimizdə ilk öncə ən az 20-30 məlumatı özündə saxlayan məlumat toplusu-**Cədvəl** olmalıdır.Bunun üçün ilk öncə tələbə cədvəlimizi yaradaq və həmçinin keçdiklərimizi xatırlayaq.

İlk öncə cədvəlimizi yaradaq.Bu nümunəmizdə tələbə cədvəlimiz aşağıdakı sütunlardan (columns) ibarət olacaqdır:
- Tələbənin adı
- Tələbənin soyadı
- Doğum tarixi
- Cinsi
- Doğum yeri
- İxtisasi
- Qrupu
> və birdə hər cədvəldə olması mütləq şəkildə lazım olan **sıra nömrəsi(Id)** sütunundan.

İndi isə gəlin uyğun tiplərin seçilməsi üçün qərar qəbul edək.

<dl>
  <dt>Id</dt>
  <dd>İlk öncə <strong>sıra nömrəsi-Id</strong> sütunu üçün hansı tip lazımdı onu seçək.İlk öncə bilirikki sıra nömrəsi rəqəm tipli məlumatdır.Ona görə də [rəqəm tipləri](/docs/datatypes.md#numerictypes) arasından uyğununu seçirik.Uyğun tipi seçmək üçün ilk öncə saxlayacağımız məlumat tipini təyin edirik.Sonra isə məlumatın həcmini.
Tələbə sistemində milyonlarda tələbə ola bilər bu o deməkdirki milyonları aşacaq bizim **Id** sütununda saxlayacağımız məlumat.Bu zaman  [Verilənlərin tipləri](/docs/datatypes.md) bölümünü birdə gözdən keçirməyimiz məsləhətdir.Seçimimizi sonradan dəyişə bilərik ama əvvəlcədən mümkün ehtimalları nəzərə almağımız məsləhətdir.Beləliklə bu qərara gəlirikki bizim <strong>sıra nömrəsi-Id</strong> sütununun tipinin <strong>int</strong> olması daha məsləhətlidir.</dd>
  
  <dt>Name</dt>
  <dd>Bu dəfə isə <strong>Tələbənin adı-Name</strong> sütunu üçün hansı tip lazımdı onu seçək.İlk öncə bilirikki tələbənin adı mətn tipli məlumatdır.Ona görə də [mətn tipləri](/docs/datatypes.md#stringtypes) arasından uyğununu seçirik.Uyğun tipi seçmək üçün ilk öncə saxlayacağımız məlumat tipini təyin edirik.Sonra isə məlumatın həcmini.Tələbənin adı mətn tiplidir və real həyatda insan adları 10-15 simvolu keçməyən hərf yığımından ibarətdir.Eyni zamanda adlar Ə,Ş kimi unicode simvolları da özündə saxlaya bilər.Bu zaman  [Verilənlərin tipləri](/docs/datatypes.md) bölümünü birdə gözdən keçirməyimiz məsləhətdir.Beləliklə bu qərara gəlirikki bizim <strong>Tələbənin adı-Name</strong> sütununun tipinin <strong>nvarchar(15)</strong> olması daha məsləhətlidir.</dd> 

  <dt>Surname</dt>
  <dd><strong>Tələbənin soyadı-Surname</strong> sütunu üçün hansı tip lazımdı onu seçək.Bu yəni soyad göstəricisinin tipi və həcmi ad göstəricisi ilə eynilik təşkil etdiyinə görə yuxarıdakı Ad üçün aldığımız qərar soyada da şamil olunur.</dd>

  <dt>BirthDate</dt>
  <dd>Bu dəfə isə <strong>Tələbənin Doğum tarixi-BirthDate</strong> sütunu üçün hansı tip lazımdı onu seçək.İlk öncə bilirikki tələbənin doğum tarixi tarix tipli məlumatdır.Ona görə də [tarix və zaman tipləri](/docs/datatypes.md#dateandtimetypes) arasından uyğununu seçirik.Uyğun tipi seçmək üçün ilk öncə saxlayacağımız məlumat tipini təyin edirik.Sonra isə məlumatın həcmini.Tələbənin doğum tarixi <i>tarix tiplidir</i>.Beləliklə bu qərara gəlirikki bizim <strong>Tələbənin Doğum tarixi-BirthDate</strong> sütununun tipinin <strong>Date</strong> olması daha məsləhətlidir.</dd>

  <dt>Gender</dt>
  <dd><strong>Tələbənin cinsi-Gender</strong> sütunu üçün hansı tip lazımdı onu seçək.Bu yəni tələbənin cinsi göstəricisinin tipi və həcmi ad göstəricisi ilə eynilik təşkil etdiyinə görə yuxarıdakı Ad üçün aldığımız qərar soyada da şamil olunur.Lakin "Kişi" və "Qadın" deyə iki cins qeyd edəcəyimizi nəzərə alsaq görərikki məlumatın həcmi maximim 5 simvol ola bilər.Bu zaman <strong>nvarchar(5)</strong> tipi seçirik bu sütun üçün.</dd>

  <dt>BirthPlace</dt>
  <dd><strong>Doğum yeri-BirthPlace</strong> sütunu üçün hansı tip lazımdı onu seçək.Bu yəni tələbənin cinsi göstəricisinin tipi və həcmi ad göstəricisi ilə eynilik təşkil etdiyinə görə yuxarıdakı Ad üçün aldığımız qərar soyada da şamil olunur.Lakin doğum yeri xanasında şəhər,rayon,qəsəbə,küçə mənzil qeyd edəcəyimizi nəzərə alsaq görərikki məlumatın həcmi orta hesabla 100+ simvol ola biler.Bu zaman <strong>nvarchar(100)</strong> tipi seçirik bu sütun üçün.</dd>


  <dt>Profession</dt>
  <dd><strong>İxtisasi-Profession</strong> sütunu üçün hansı tip lazımdı onu seçək.Cavabınızı eşidir kimiyəm.Bəli yenə mətn tipli məlumatdir.100-150 simvolluq həcmə malik olacaq.Ümumiyyətlə nvarchar tipi variable-Length(yəni yazılmış məlumatın uzunluğu qədər yer tutur) olduğu üçün max uzunluğun çox götürsək fövqaladə problem yaratmış olmarıq.Beləliklə sütunun tipini <strong>nvarchar(150)</strong> seçirik.</dd>


  <dt>Group</dt>
  <dd>Son olaraq <strong>Qrupu-Group</strong> sütunu üçün hansı tip lazımdı onu seçək.Mətn tipli olduğu üçün və "A0000" kimi məlumat saxlayacaöğımızı nəzərə alaraq mətn tipli sahə ayıracağımızı bilirik və həcmi 5 simvol kimi qəbul edirik.Beləliklə sütunun tipini <strong>varchar(5)</strong> seçirik,ona görə ki, unicode simvollara ehtiyyac olmur bu sahə-Group üzrə.</dd>

</dl>



