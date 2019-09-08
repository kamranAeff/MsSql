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

    <pre>
    Cannot insert the value NULL into column 'Name', table 'Intelect.dbo.Category'; column does not allow nulls. INSERT fails.
    <pre>
```


<h2 id="uniquekey"></h2>


<h2 id="primarykey"></h2>


<h2 id="check"></h2>


<h2 id="foreignkey"></h2>