# Table əməliyyatları / Verilənlərin tipləri - DataTypes

Sql Serverdə Məlumatların saxlanılmasında əsas və yeganə rolu cədvəllər(Table) oynayır.Məlumatlar cədvəllərdə sətirlər(row/record) şəklində saxlanılır. Və hər məlumat hissələrə (xüsusiyyətlərə) ayrılaraq saxlanılır.Bu hissələrin də təyinatına görə yaddaşda saxlanılması zərürəti yaradılır.Bu zərurəti qarşılamaq üçün verilənlərin tipi anlayışı meydana gəlir.Verilənlərin tipləri təyinatına görə aşağıdakı növlərə bölünür:

## String Datatypes
#### Aşağıda göstərilən mətn tipləri mövcuddur

<table>
  <thead>
  <tr>
    <th>Adı</th>
    <th>Ölçüsü</th>
    <th>Təyini</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>CHAR(<em>size</em>)</td>
    <td>Maksimal simvol sayı 8000-dir.</td>
    <td>Verdiyimiz ölçü qədər(Fixed-length) yaddaşda yer zəbt edir hər sətir üçün.Əgər <strong>CHAR(8)</strong> yazıb 5 simvolluq "dərs" sözünü saxlayırıqsa qalan 3 simvolu boşluqla doldurur.Unikod məlumatları saxlamır.</td>
  </tr>
  <tr>
    <td>VARCHAR(<em>size</em>) or VARCHAR(max)</td>
    <td>Maksimal simvol sayı 8000-dir.</td>
    <td><strong>CHAR</strong>-tipindən fərqli olaraq verdiyimiz ölçü qədər yox məlumatın ölçüsü qədər(Variable-length) yaddaşda yer zəbt edir hər sətir üçün.Əgər <strong>VARCHAR(8)</strong> yazıb 5 simvolluq "dərs" sözünü saxlayırıqsa qalan 3 simvolluq yeri azad buraxır.<strong>VARCHAR(max)</strong> deyə təyin etdikdə isə maksimal 2GB-lıq məlumat yadda saxlaya bilərik.Unikod məlumatları saxlamır.</td>
  </tr>
  <tr>
    <td>TEXT</td>
    <td>Maksimal məlumat ölçüsü 2GB-dır.</td>
    <td>Variable-length məlumat tipidir. Unikod məlumatları saxlamır.</td>
  </tr>
  <tr>
    <td>NCHAR(<em>size</em>)</td>
    <td>Maksimal simvol sayı 4000-dir.</td>
    <td>Fixed-length məlumat tipidir. Unikod məlumatları saxlayır.</td>
  </tr>
  <tr>
    <td>NVARCHAR(<em>size</em>) or NVARCHAR(max)</td>
    <td>Maksimal simvol sayı 4000-dir.</td>
    <td>Variable-length məlumat tipidir.Maksimal 2GB-lıq məlumat yadda saxlaya bilərik.Unikod məlumatları saxlayır.</td>
  </tr>
  <tr>
    <td>NTEXT</td>
    <td>Maksimal byte sayı 1.073.741.823-dir.</td>
    <td>Variable-length məlumat tipidir.Unikod məlumatları saxlayır.</td>
  </tr>
  <tr>
    <td>BINARY(<em>size</em>)</td>
    <td>Maksimal simvol sayı 8000-dir.</td>
    <td>Fixed-length məlumat tipidir.</td>
  </tr>
  <tr>
    <td>VARBINARY(<em>size</em>) or VARBINARY(max)</td>
    <td>Maksimal simvol sayı 8000-dir.</td>
    <td>Variable-length məlumat tipidir.<strong>VARBINARY(max)</strong> deyə təyin etdikdə isə maksimal 2GB-lıq məlumat yadda saxlaya bilərik.</td>
  </tr>
  <tr>
    <td>IMAGE</td>
    <td>Maksimal məlumat ölçüsü 2GB-dır.</td>
    <td>Variable-length məlumat tipidir.</td>
  </tr>
  </tbody>
</table>


## Numeric Datatypes
#### Aşağıda göstərilən rəqəmsal tiplər mövcuddur

<table>
  <thead>
  <tr>
    <th>Adı</th>
    <th>Ölçüsü</th>
    <th>Təyini</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>BIT</td>
    <td>Tam ədədlərdən 0, 1, ya da NULL qiymətlərini alır.</td>
    <td></td>
  </tr>
  <tr>
    <td>TINYINT</td>
    <td>0 - 255</td>
    <td></td>
  </tr>
  <tr>
    <td>SMALLINT</td>
    <td>-32768 - 32767</td>
    <td></td>
  </tr>
  <tr>
    <td>INT</td>
    <td>-2,147,483,648 - 2,147,483,647</td>
    <td></td>
  </tr>
  <tr>
    <td>BIGINT</td>
    <td>-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</td>
    <td></td>
  </tr>
  <tr>
    <td>DECIMAL(<em>m</em>,<em>d</em>)</td>
    <td><em><strong>m</strong></em> susmaya görə dəyəri 18 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.<br>
    <em><strong>d</strong></em> susmaya görə dəyəri 0 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.</td>
    <td><em><strong>m</strong></em> ümumi simvol sayıdır <em><strong>d</strong></em> isə kəsr hissəyə aid olan simvol sayı.<br></td>
  </tr>
  <tr>
    <td>DEC(<em>m</em>,<em>d</em>)</td>
    <td><em><strong>m</strong></em> susmaya görə dəyəri 18 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.<br>
    <em><strong>d</strong></em> susmaya görə dəyəri 0 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.</td>
    <td><em><strong>m</strong></em> ümumi simvol sayıdır <em><strong>d</strong></em> isə kəsr hissəyə aid olan simvol sayı.<br>Bu tip Decimal tipin sinonimidir.</td>
     <td></td>
  </tr>
  <tr>
    <td>NUMERIC(<em>m</em>,<em>d</em>)</td>
    <td><em><strong>m</strong></em> susmaya görə dəyəri 18 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.<br>
    <em><strong>d</strong></em> susmaya görə dəyəri 0 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.</td>
    <td><em><strong>m</strong></em> ümumi simvol sayıdır <em><strong>d</strong></em> isə kəsr hissəyə aid olan simvol sayı.<br>
    <br>Bu tip Decimal tipin sinonimidir.</td>
  </tr>
  <tr>
    <td>FLOAT(<em>n</em>)</td>
    <td>Sürüşkən nöqtəli ədədir.<br> <em><strong>n</strong></em> susmaya görə dəyəri 53 qəbul edilir, əks halda biz qeyd etdiyimiz ölçü.</td>
    <td></td>
  </tr>
  <tr>
    <td>REAL</td>
    <td>FLOAT(24)`ə ekvavalentdir</td>
    <td></td>
  </tr>
  <tr>
    <td>SMALLMONEY</td>
    <td>- 214,748.3648 - 214,748.3647</td>
    <td></td>
  </tr>
  <tr>
    <td>MONEY</td>
    <td>-922,337,203,685,477.5808 - 922,337,203,685,477.5807</td>
    <td></td>
  </tr>
  </tbody>
</table>

## Date/Time Datatypes
#### Aşağıda göstərilən tarix və zaman tiplər mövcuddur

<table>
  <thead>
  <tr>
    <th>Adı</th>
    <th>Ölçüsü</th>
    <th>Təyini(tətbiq olunsa)</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>DATE</td>
    <td>'0001-01-01' - '9999-12-31'.</td>
    <td>Görünüşü 'YYYY-MM-DD'</td>
  </tr>
  <tr>
    <td>DATETIME</td>
    <td>'1753-01-01 00:00:00' - '9999-12-31 23:59:59'.<br>
    <td>Görünüşü 'YYYY-MM-DD hh:mm:ss[.mmm]'</td>
  </tr>
  <tr>
    <td>DATETIME2(<em>saniyə dəqiqlik dərəcəsi</em>)</td>
    <td>'0001-01-01' - '9999-12-31'.</td>
    <td>Görünüşü 'YYYY-MM-DD hh:mm:ss[.fractional seconds]'</td>
  </tr>
  <tr>
    <td>SMALLDATETIME</td>
    <td>'1900-01-01' - '2079-06-06'.</td>
    <td>Görünüşü 'YYYY-MM-DD hh:mm:ss'</td>
  </tr>
  <tr>
    <td>TIME</td>
    <td>'00:00:00.0000000' - '23:59:59.9999999'</td>
    <td>Görünüşü 'YYYY-MM-DD hh:mm:ss[.nnnnnnn]'</td>
  </tr>
  <tr>
    <td>DATETIMEOFFSET(<em>saniyə dəqiqlik dərəcəsi</em>)</td>
    <td>'0001-01-01' - '9999-12-31'.<br>
        Zonaya görə saat fərqi -14:00 to +14:00.</td>
    <td>Görünüşü 'YYYY-MM-DD hh:mm:ss[.nnnnnnn]' [{+|-}hh:mm]</td>
  </tr>
  </tbody>
</table>
