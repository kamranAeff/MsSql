# Table əməliyyatları / Verilənlərin tipləri - DataTypes

Sql Serverdə Məlumatların saxlanılmasında əsas və yeganə rolu cədvəllər(Table) oynayır.Məlumatlar cədvəllərdə sətirlər(row/record) şəklində saxlanılır. Və hər məlumat hissələrə (xüsusiyyətlərə) ayrılaraq saxlanılır.Bu hissələrin də təyinatına görə yaddaşda saxlanılması zərürəti yaradılır.Bu zərurəti qarşılamaq üçün verilənlərin tipi anlayışı meydana gəlir.Verilənlərin tipləri təyinatına görə aşağıdakı növlərə bölünür:

## String Datatypes
#### Aşağıda göstərilən mətn tipləri mövcuddur
<table>
  <thead>
  <tr>
    <th>Data Type Syntax</th>
    <th>Maximum Size</th>
    <th>Explanation</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>CHAR(<em>size</em>)</td>
    <td>Maximum size of 8,000 characters.</td>
    <td>Where <strong><em>size</em></strong> is the number of characters to store. Fixed-length. Space padded on right to equal <em><strong>size</strong></em> characters. Non-Unicode data.</td>
  </tr>
  <tr>
    <td>VARCHAR(<em>size</em>) or VARCHAR(max)</td>
    <td>Maximum size of 8,000 or max characters.</td>
    <td>Where <strong><em>size</em></strong> is the number of characters to store. Variable-length. If <em>max</em> is specified, the maximum number of characters is 2GB. Non-Unicode data.</td>
  </tr>
  <tr>
    <td>TEXT</td>
    <td>Maximum size of 2GB.</td>
    <td>Variable-length. Non-Unicode data.</td>
  </tr>
  <tr>
    <td>NCHAR(<em>size</em>)</td>
    <td>Maximum size of 4,000 characters.</td>
    <td>Fixed-length. Unicode data.</td>
  </tr>
  <tr>
    <td>NVARCHAR(<em>size</em>) or NVARCHAR(max)</td>
    <td>Maximum size of 4,000 or max characters.</td>
    <td>Where <strong><em>size</em></strong> is the number of characters to store. Variable-length. If <em>max</em> is specified, the maximum number of characters is 2GB. Unicode data.</td>
  </tr>
  <tr>
    <td>NTEXT</td>
    <td>Maximum size of 1,073,741,823 bytes.</td>
    <td>Variable length. Unicode data.</td>
  </tr>
  <tr>
    <td>BINARY(<em>size</em>)</td>
    <td>Maximum size of 8,000 characters.</td>
    <td>Where <strong><em>size</em></strong> is the number of characters to store. Fixed-length. Space padded on right to equal <em><strong>size</strong></em> characters. Binary data.</td>
  </tr>
  <tr>
    <td>VARBINARY(<em>size</em>) or VARBINARY(max)</td>
    <td>Maximum size of 8,000 or max characters.</td>
    <td>Where <strong><em>size</em></strong> is the number of characters to store. Variable-length. If <em>max</em> is specified, the maximum number of characters is 2GB. Non-Binary data.</td>
  </tr>
  <tr>
    <td>IMAGE</td>
    <td>Maximum size of 2GB.</td>
    <td>Variable length . Binary data.</td>
  </tr>
  </tbody>
</table>


## Numeric Datatypes
#### Aşağıda göstərilən rəqəmsal tiplər mövcuddur

<table>
  <thead>
  <tr>
    <th>Data Type Syntax</th>
    <th>Maximum Size</th>
    <th>Explanation</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>BIT</td>
    <td>Integer that can be 0, 1, or NULL.</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>TINYINT</td>
    <td>0 to 255</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>SMALLINT</td>
    <td>-32768 to 32767</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>INT</td>
    <td>-2,147,483,648 to 2,147,483,647</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>BIGINT</td>
    <td>-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>DECIMAL(<em>m</em>,<em>d</em>)</td>
    <td><em><strong>m</strong></em> defaults to 18, if not specified.<br>
    <em><strong>d</strong></em> defaults to 0, if not specified.</td>
    <td>Where <em><strong>m</strong></em> is the total digits and <em><strong>d</strong></em> is the number of digits after the decimal.<br></td>
  </tr>
  <tr>
    <td>DEC(<em>m</em>,<em>d</em>)</td>
    <td><em><strong>m</strong></em> defaults to 18, if not specified.<br>
    <em><strong>d</strong></em> defaults to 0, if not specified.</td>
    <td>Where <em><strong>m</strong></em> is the total digits and <em><strong>d</strong></em> is the number of digits after the decimal.<br>
    <br>
        This is a synonym for the DECIMAL datatype.</td>
  </tr>
  <tr>
    <td>NUMERIC(<em>m</em>,<em>d</em>)</td>
    <td><em><strong>m</strong></em> defaults to 18, if not specified.<br>
    <em><strong>d</strong></em> defaults to 0, if not specified.</td>
    <td>Where <em><strong>m</strong></em> is the total digits and <em><strong>d</strong></em> is the number of digits after the decimal.<br>
      <br>
This is a synonym for the DECIMAL datatype.</td>
  </tr>
  <tr>
    <td>FLOAT(<em>n</em>)</td>
    <td>Floating point number.<br>
     <em><strong>n</strong></em> defaults to 53, if not specified.</td>
    <td>Where <em><strong>n</strong></em> is the number of number of bits to store in scientific notation.</td>
  </tr>
  <tr>
    <td>REAL</td>
    <td>Equivalent to FLOAT(24)</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>SMALLMONEY</td>
    <td>- 214,748.3648 to 214,748.3647</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>MONEY</td>
    <td>-922,337,203,685,477.5808 to 922,337,203,685,477.5807</td>
    <td>&nbsp;</td>
  </tr>
  </tbody>
</table>