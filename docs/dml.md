# Qeydiyyat ifadələri

Sql server`də yeni məlumatların qeydiyyatı,mövcud məlumatların redaktə edilməsi və lazımsız məlumatların silinməsi üçün DML(Data Manipulation Language) bölməsinə aid komandalar istifadə olunur.Bu bölməyə aşağıdakı komandalar aiddir:

- Insert    - Yeni məlumatların əlavə edilməsi
- Update    - Mövcud məlumatların redaktəsi
- Delete    - Lazımsız məlumatların silinməsi

Əslində əlavə olaraq bir komanda da var bu siyahıya aid olan- **Select**,lakin biraz fərqli və geniş işlənmə qaydalarına malik olan komanda olduğundan növbəti məqaləni ona həsr edəcəyik.

<h2 id="insert">INSERT INTO</h2>

Daha öncə qısa olaraq **Insert** komandasının yeni məlumatların əlavə edilməsi üçün istifadə etdiyimizi vurğulamışdıq.İndi isə bu komandadan necə istifadə edəcəyimizi əyani şəkildə göstərək.Şablon aşağıdakı kimidir:

```html
    use [Intelect];
    go
    insert into <cedvel_adi>(<,sutunların_siyahısı>) 
    values({DEFAULT|NULL},..,.[Deyerlerin siyahısı]);
    go
```

Daha öncə yaratdığımız **Category** cədvəlinə məlumat əlavə etmək üçün insert komandasını istifadə edək
```html
    use [Intelect];
    go
    insert into [Category]([Id],[Name]) values(1,N'Ofis Ləvazimatları');
    insert into [Category]([Id],[Name]) values(2,N'Məişət Əşyaları');

    insert into [Category]([Id],[Name],[CreatedDate]) values(3,N'Akksesuarlar',DEFAULT);
    go
```

Yoxlamaq üçün **Select** komandasından istifadə edək

```html
    use [Intelect];
    go
    select * from [Category];
    go
```

<h2 id="update">UPDATE</h2>

Daha öncə qısa olaraq **Update** komandasının mövcud məlumatların redaktəsi üçün istifadə etdiyimizi vurğulamışdıq.İndi isə bu komandadan necə istifadə edəcəyimizi əyani şəkildə göstərək.Şablon aşağıdakı kimidir:


```html
    use [Intelect];
    go
    update <cedvel_adi>
    set <redakte_edilecek_sutun_adı>=<yeni_deyeri>
    where <redaktə_olunacaq_məlumatların_seçim_şərtləri>;
    go
```

**Category** cədvəlində id`si 3 olan kategoriyanın adının "telefon aksessuarları"-na dəyişdirilməsi üçün bu komandanı icra edək

```html
    use [Intelect];
    go
    update [Category]
    set [Name]=N'telefon aksessuarları'
    where [Id]=3;
    go
```

eyni anda bir neçə sütunun dəyərini dəyişə bilərik

```html
    use [Intelect];
    go
    update [Category]
    set [Name]=N'yeni telefon aksessuarları',[CreatedDate]='2019-09-09'
    where [Id]=3;
    go
```

> Ama seçim şərtini qeyd etmədən bu komandanı icra etsəz bu zaman cədvəldəki bütün sətirlərə eyni məlumatı yazacaq,və bu da öncəki məlumatların itirilməsinə gətirib çıxaracaq ki, bu da sizin üçün təhlükəlidir.


<h2 id="delete">DELETE</h2>

Daha öncə qısa olaraq **Delete** komandasının lazımsız məlumatların silinməsi üçün istifadə etdiyimizi vurğulamışdıq.İndi isə bu komandadan necə istifadə edəcəyimizi əyani şəkildə göstərək.Şablon aşağıdakı kimidir:

```html
    use [Intelect];
    go
    delete from <cedvel_adi>
    where <redaktə_olunacaq_məlumatların_seçim_şərtləri>;
    go
```

**Category** cədvəlindən id`si 2 olan kategoriyanın silinməsi üçün bu komandanı icra edək

```html
    use [Intelect];
    go
    delete from [Category]
    where [Id]=2;
    go
```

> Ama seçim şərtini qeyd etmədən bu komandanı icra etsəz bu zaman cədvəldəki bütün sətirləri siləcək,və bu da öncəki məlumatların itirilməsinə gətirib çıxaracaq ki, bu da sizin üçün təhlükəlidir.