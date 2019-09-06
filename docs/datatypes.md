# Table əməliyyatları / Verilənlərin tipləri - DataTypes

Sql Serverdə Məlumatların saxlanılmasında əsas və yeganə rolu cədvəllər(Table) oynayır.Məlumatlar cədvəllərdə sətirlər(row/record) şəklində saxlanılır. Və hər məlumat hissələrə (xüsusiyyətlərə) ayrılaraq saxlanılır.Bu hissələrin də təyinatına görə yaddaşda saxlanılması zərürəti yaradılır.Bu zərurəti qarşılamaq üçün verilənlərin tipi anlayışı meydana gəlir.Verilənlərin tipləri təyinatına görə aşağıdakı növlərə bölünür:

## String Datatypes

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
