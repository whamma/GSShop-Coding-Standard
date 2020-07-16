# GSShop-Coding-Standard

## Contents
## PHP
[PSR-1(Basic Coding Standard)](#psr-1basic-coding-standard)

[1. Overview](#1-overview)

[2. Files](#2-files)

[2.1 PHP 태그](#21-php-태그)

[2.2 문자 인코딩](#22-문자-인코딩)

[2.3 Side Effects](#23-side-effects)

[3. Namespace and Class Names](#3-namespace-and-class-names)

[4. Class Constants, Properties, and Methods](#4-class-constants-properties-and-methods)

[PSR-2(Coding Style Guide)](#psr-2coding-style-guide)

[PSR-3(Basic Coding Standard)](#psr-3logger-interface)

[PSR-4(Basic Coding Standard)](#psr-4autoloader)

## laravel
[단일 책임 원칙](#단일-책임-원칙)

[모델은 무겁게, 컨트롤러는 가볍게](#모델은-무겁게-컨트롤러는-가볍게)

[Validation-유효성 검사](#validation-유효성-검사)

[비즈니스 로직은 서비스 클래스에 있어야 합니다.](#비즈니스-로직은-서비스-클래스에-있어야-합니다)

[중복 배제(Don't repeat yourself)](#중복-배제dont-repeat-yourself)

[Query Builder, raw SQL 쿼리보다 Eloquent를 사용하는 것이 좋습니다.](#query-builder-raw-sql-쿼리보다-eloquent를-사용하는-것이-좋습니다)

[Mass assignment-대량 할당](#mass-assignment-대량-할당)

[블레이드 템플릿에서 쿼리를 실행하지 않습니다. 그리고 즉시 로딩을 사용합니다.(N + 1 문제)](#블레이드-템플릿에서-쿼리를-실행하지-않습니다-그리고-즉시-로딩을-사용합니다n--1-문제)

[코드에 주석을 작성합니다. 하지만 주석보다 의미있는 메서드 이름과 변수 이름을 사용하는 것이 더 좋습니다.](#코드에-주석을-작성합니다-하지만-주석보다-의미있는-메서드-이름과-변수-이름을-사용하는-것이-더-좋습니다)

[블레이드 템플릿에 JS와 CSS를 작성하지 않고 PHP 클래스에 HTML을 작성하지 않습니다.](#블레이드-템플릿에-js와-css를-작성하지-않고-php-클래스에-html을-작성하지-않습니다)

[코드에 텍스트로 작성하지 않고, 설정 파일, 언어 파일, 상수 등을 사용합니다.](#코드에-텍스트로-작성하지-않고-설정-파일-언어-파일-상수-등을-사용합니다)

[라라벨 커뮤니티에서 수용하는 표준 라라벨 도구를 사용합니다.](#라라벨-커뮤니티에서-수용하는-표준-라라벨-도구를-사용합니다)

[라라벨 네이밍 규칙을 따릅니다.](#라라벨-네이밍-규칙을-따릅니다)

[될 수 있으면 짧고 읽기 쉬운 문법을 사용합니다.](#될-수-있으면-짧고-읽기-쉬운-문법을-사용합니다)

[new Class 대신 IoC 컨테이너 또는 파사드를 사용합니다.](#new-class-대신-ioc-컨테이너-또는-파사드를-사용합니다)

[.env 파일에서 직접 데이터를 가져오지 않습니다.](#env-파일에서-직접-데이터를-가져오지-않습니다)

[날짜를 표준 형식으로 저장합니다. accessors(get), mutators(set)을 사용해 날짜 형식을 수정합니다.](#날짜를-표준-형식으로-저장합니다-accessorsget-mutatorsset을-사용해-날짜-형식을-수정합니다)

[또 다른 좋은 사례](#또-다른-좋은-사례)

### **PSR-1(Basic Coding Standard)**

### 1. Overview
* 파일은 태그 <?php와 <?=태그만 사용해야 합니다.
* 파일은 PHP 코드에 BOM없이 UTF-8 만 사용해야합니다.
* 파일은 기호 (클래스, 함수, 상수 등) 를 선언 하거나 side effects (예 : 출력 생성, .ini 설정 변경 등)을 이야기해야하지만 둘 다 수행해서는 안됩니다.
* 네임 스페이스와 클래스는 반드시 "autoloading" PSR [ PSR-0 , PSR-4 ]을 따라야합니다.
* 클래스 이름은 반드시 StudlyCaps를 따라야 한다.
* 클래스 상수는 모두 대문자로 밑줄 구분 기호로 선언해야합니다.
* 메서드 이름은 반드시 camelCase에서 선언해야합니다.
### 2. Files
 #### 2.1 PHP 태그
  * PHP 코드는 긴 태그 또는 짧은 에코 태그를 사용해야합니다.
  * 다른 태그 변형을 사용해서는 안됩니다. <?php ?><?= ?>

 #### 2.2 문자 인코딩
  * PHP 코드는 BOM (Byte Order Mark) UTF-8 만 사용해야합니다.

 #### 2.3 Side Effects
  * 빈 구문이 아니라면 반드시 하나의 side effect를 가져야합니다.

  >"All non null statements shall potentially have a side effect"
  >>_"실행 중에 어떤 객체를 접근해서 변화가 일어나는 행위"
  "Accessing an object designated by a volatile lvalue, modifying an object, calling a library I/O function, or calling a function that does any of those operations are all side effects, which are changes in the state of the execution environment."_

   * 파일은 새로운 기호 (클래스, 함수, 상수 등)를 선언하고 다른 부작용을 일으키지 않아야하며, side effects가 있는 로직을 실행해야하지만 두 가지를 모두 실행해서는 안된다.

   * "side effects"는 단지 클래스, 함수, 상수 등을 선언하는 것과 직접적으로 관련이없는 로직의 실행을 파일을 포함하는 것을 의미합니다 .

   * "side effects"에는 출력 생성, 명시 적 사용 require또는 include의 외부 서비스 연결, ini 설정 수정, 오류 또는 예외 처리, 전역 변수 또는 정적 변수 [수정, 파일 읽기 또는 쓰기] 등 이 포함되지만 이에 국한 되지는 않습니다 . 다음은 선언과 side effects가 모두 포함 된 파일의 예제입니다.
 
  예제 :
 
   ```php
   <?php
   // side effect: change ini settings
   ini_set('error_reporting', E_ALL);

   // side effect: loads a file
   include "file.php";

   // side effect: generates output
   echo "<html>\n";

   // declaration
   function foo()
   {
    // function body
   }
   ```
다음 예제는 side effects가 없는 선언 파일입니다.

예제 : 

```php
<?php
// declaration
function foo()
{
    // function body
}

// conditional declaration is *not* a side effect
if (! function_exists('bar')) {
    function bar()
    {
        // function body
    }
}
```

### 3. Namespace and Class Names
 #### 3.1 네임 스페이스와 클래스는 반드시 "autoloading" PSR [ PSR-0 , PSR-4 ]을 따라야합니다.
  * 이것은 각 클래스가 하나의 파일에 있고 적어도 한 수준의 네임 스페이스, 즉 최상위 벤더 이름에 있음을 의미합니다. 클래스 이름은에서 선언되어야 StudlyCaps합니다. PHP 5.3 및 이후 버전 용으로 작성된 코드는 정식 네임 스페이스를 사용해야합니다.

예제:

```php
<?php
// PHP 5.3 and later:
namespace Vendor\Model;

class Foo
{
}
```
php ver.5.2.x 로 작성된 코드는 클래스 이름에 Vendor_ 접두어의 의사 네임 스페이스 규칙을 사용해야합니다.

```php
<?php
// PHP 5.2.x and earlier:
class Vendor_Model_Foo
{
}
```

### 4. Class Constants, Properties, and Methods
 "Class"라는 용어는 모든 Class, interfaces 및 특성을 나타냅니다.
 #### 4.1 상수
  * 클래스 상수는 밑줄 구분 기호로 모든 대문자에서 선언되어야 합니다.

예제 : 

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

 #### 4.2. 특성 본 가이드는 $StudlyCaps, $camelCass, $under_score 속성 이름의 사용에 관한 권고를 의도적으로 회피한다.
  * 어떤 명명 규칙을 사용하든 적절한 범위 내에서 일관성 있게 적용해야 한다. 이 범위는 공급업체 수준, 패키지 수준, 클래스 수준 또는 방법 수준일 수 있다.
 #### 4.3. 방법 Method name은 반드시 camelCase()로 선언해야 합니다.

[🔝 목차로 돌아가기](#contents)
### **PSR-2(Coding Style Guide)**
 PSR-1을 기본으로 추가적인 요구사항들을 가이드 한다.
### 1. Overview
* 코드는 반드시 "코딩 스타일 가이드"인 PSR [ PSR-1 ]을 따라야합니다.
* 코드는 탭이 아닌 들여 쓰기에 4 칸을 사용해야합니다.
* 라인 길이에 엄격한 제한이 있어서는 안됩니다. 소프트 한도는 120 자 여야합니다 (MUST). 줄은 80 자 이하 여야합니다 (권장하지 않는다).
* namespace선언 뒤에 빈 줄 이 하나 있어야하며 use선언 블록 뒤에 빈 줄이 하나 있어야합니다 .
* 클래스를 여는 중괄호는 반드시 다음 줄로 가야하며, 닫는 중괄호는 본문 뒤의 다음 줄로 가야합니다.
* 메소드의 여는 중괄호는 반드시 다음 줄로 가야하며 닫는 중괄호는 반드시 본문 뒤에 오는 다음 줄로 가야합니다.
* 가시성 (visibility)은 모든 속성과 메소드에서 반드시 선언되어야한다. abstract및 final가시성 전에 선언해야합니다. static 가시성 뒤에 선언해야합니다.
* 제어 구조 키워드는 그 뒤에 하나의 공백을 가져야합니다. 메서드와 함수 호출은해서는 안된다.
* 제어 구조의 여는 중괄호는 반드시 같은 줄에 있어야하며, 닫는 중괄호는 본문 뒤의 다음 줄로 가야합니다.
* 제어 구조에 대한 여는 괄호는 그 뒤에 공백이 없어야하며, 제어 구조의 닫는 괄호는 전에는 공백이 없어야합니다 (요구하지 말아야한다).

예제 : 

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleMethod($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

### 2. General
 #### 2.1.Basic Coding Standard
  * 코드는 PSR-1에 설명 된 모든 규칙을 따라야합니다 .
 #### 2.2.Files
  * 모든 PHP 파일은 Unix LF (linefeed) 줄 끝을 사용해야합니다.
  * 모든 PHP 파일은 하나의 빈 줄로 끝나야합니다.
  * 닫기 ?> 태그는 PHP 만 포함 된 파일에서 생략해야합니다 (MUST).
 #### 2.3.Lines
  * 라인 길이에 엄격한 제한이 있어서는 안됩니다.
  * 줄 길이에 대한 소프트 제한은 120 자 여야합니다. 자동화 된 스타일 체커는 반드시 경고해야하지만 소프트 한도에서 오류를 나타내지 않아야합니다.
  * 행은 80자를 넘지 않아야합니다 (SHOULD NOT). 그보다 긴 행은 각각 80 문자 이하의 여러 행으로 나눠 져야합니다 (SHOULD).
  * 비어 있지 않은 줄 끝에는 공백 문자가 없어야합니다.
  * 가독성을 높이고 관련 코드 블록을 나타 내기 위해 빈 줄을 추가 할 수 있습니다 (MAY).
  * 한 줄에 하나 이상의 문장이 있어서는 안됩니다.
 #### 2.4.Indenting
  * 코드는 반드시 4 칸의 들여 쓰기를 사용해야하며, 들여 쓰기에는 탭을 사용하지 않아야합니다.
  * Nb : 공백만을 사용하고 탭과 공백을 섞지 않으면, diff, 패치, 히스토리 및 주석 문제를 피할 수 있습니다. 공백을 사용하면 행간 정렬을 위해 세분화 된 하위 들여 쓰기를 쉽게 삽입 할 수 있습니다.
 #### 2.5.Keywords and True/False/Null
  * PHP 키워드 는 소문자 여야합니다. PHP 상수 true,, false및 null은 소문자 여야합니다.
 #### 2.6.Namespace and Use Declarations
  * 존재할 때 namespace선언 다음에 빈 줄이 하나 있어야합니다.
  * 이 use선언 이 존재하면 모든 선언은 반드시 선언을 따라야합니다 namespace.
  * use선언 당 하나의 키워드가 있어야합니다.
  * use블록 다음에 빈 줄이 하나 있어야합니다.
 #### 2.7.Classes, Properties, and Methods
  * 클래스는 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메소드(method)로 구성됩니다. 즉, 필드(field)란 클래스에 포함된 변수(variable)를 의미합니다.
  * 메소드(method)란 어떠한 특정 작업을 수행하기 위한 명령문의 집합이라 할 수 있습니다
 
  2.7.1. Extends and Implements
   * extends및 implements키워드는 클래스 이름과 같은 줄에 선언해야합니다. 해당 클래스의 여는 중괄호는 자체 줄에 있어야합니다. 클래스의 닫는 중괄호는 본문 뒤의 다음 줄로 가야합니다. 
  
 예제 :

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```
목록은 implements 각각의 후속 행 일단 들여되는 여러 줄에 걸쳐 분할 될 수있다. 그렇게 할 때 목록의 첫 번째 항목은 다음 줄에 있어야하며 한 줄에 하나의 인터페이스만 있어야합니다.

예제 :

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```
  2.7.2.Properties
   * 모든 속성에서 가시성을 반드시 선언해야합니다. var키워드는 속성을 선언하는 데 사용되어서는 안된다. 명령문마다 하나 이상의 속성이 선언되어서는 안됩니다. 프로퍼티 이름은 보호 된 프라이빗 가시성 또는 프라이빗 가시성을 나타 내기 위해 하나의 밑줄로 접두어를 사용해서는 안됩니다 (SHOULD NOT). 속성 선언은 다음과 같습니다.
   
   예제:
   
   ```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

  2.7.3.Methods
   * 모든 메소드에서 가시성을 선언해야합니다 (MUST). 메소드 이름은 보호되거나 개인적인 가시성을 나타 내기 위해 하나의 밑줄로 접두어를해서는 안됩니다 (SHOULD NOT). 메서드 이름은 메서드 이름 다음에 공백으로 선언하면 안됩니다 (MUST NOT). 여는 중괄호는 반드시 자신의 줄에 있어야하며 닫는 중괄호는 반드시 그 다음 줄에 있어야합니다. 여는 괄호 뒤에 공백이 있으면 안되며 닫는 괄호 앞에 공백이 있어서는 안됩니다.
   >메소드 선언은 다음과 같습니다. 괄호, 쉼표, 공백 및 중괄호의 배치에 유의하십시오.
  
```php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

  2.7.4.Method Arguments
   * 인수 목록에서 각 쉼표 앞에 공백이 있으면 안되며 각 쉼표 뒤에 하나의 공백이 있어야합니다. 디폴트 값을 가진 메소드 인수는 인수 목록의 끝에 와야합니다 (MUST).

예제:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```
인수 목록은 여러 줄에 걸쳐 나뉘어 질 수 있으며, 각 줄은 한 번 들여 쓰여질 수 있습니다. 그렇게 할 때 목록의 첫 번째 항목은 다음 줄에 있어야하며 한 줄에 하나의 인수 만 있어야합니다.

인수 목록이 여러 줄에 걸쳐 분할되어 있으면 닫는 괄호와 여는 중괄호는 한 줄의 공백을 사용하여 각각의 줄에 함께 있어야합니다 (MUST).

예제:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```
  2.7.5.abstract, final, and static
   * 존재하는 경우, abstract및 final선언은 가시성 선언 앞에 와야합니다 (MUST). 현재 static선언이 가시성 선언 뒤에 와야합니다.
  ```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

  2.7.6.Method and Function Calls
   * 메서드 나 함수 호출을 할 때 메서드 나 함수 이름과 여는 괄호 사이에 공백이 없어야합니다. 여는 괄호 뒤에 공백이 있으면 안되며 닫는 괄호 앞에 공백이 있어서는 안됩니다. 인수 목록에서 각 쉼표 앞에 공백이 있으면 안되며 각 쉼표 뒤에 하나의 공백이 있어야합니다.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

인수 목록은 여러 줄에 걸쳐 나뉘어 질 수 있으며, 각 줄은 한 번 들여 쓰여질 수 있습니다. 그렇게 할 때 목록의 첫 번째 항목은 다음 줄에 있어야하며 한 줄에 하나의 인수 만 있어야합니다.
```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```
### 3.Control Structures
 > 제어 구조의 일반적인 스타일 규칙은 다음과 같습니다.
  * 제어 구조 키워드 다음에 하나의 공백이 있어야합니다
  * 여는 괄호 뒤에 공백이 있으면 안됩니다 (MUST NOT).
  * 닫는 괄호 앞에 공백이 있어서는 안됩니다 (MUST NOT).
  * 닫는 괄호와 여는 중괄호 사이에 하나의 공백이 있어야합니다.
  * 구조체는 한 번 들여 쓰기되어야합니다 (MUST).
  * 닫는 중괄호는 몸체 뒤의 다음 줄에 있어야합니다.
 각 구조의 몸체는 중괄호로 묶어야합니다 (MUST). 이것은 구조가 어떻게 보이는지를 표준화하고 새로운 라인이 몸에 추가 될 때 오류가 발생할 가능성을 줄입니다.
 #### 3.1.if, elseif, else
  * if구조는 다음과 같다. 괄호, 공백 및 중괄호의 배치에 유의하십시오. 그 else와 elseif이전 몸 닫는 중괄호 동일한 행에있다.
  
  예제 : 
  ```php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```
모든 제어 키워드가 단일 단어처럼 보이도록 elseif 대신 else if라고 규정하는게 좋습니다.
 #### 3.2.switch, case
  * 스위치 구조는 다음과 같습니다. 괄호, 공백 및 중괄호의 배치에 유의하십시오. case 문은 스위치에서 한 번 들여 쓰기되어야하며, break 키워드 (또는 다른 종료 키워드)는 사례 본문과 동일한 수준에서 들여 쓰기되어야합니다 (MUST). 비어 있지 않은 케이스 본문에서 fall-through가 의도적 일 때 // break와 같은 코멘트가 있어야합니다.

예제:

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```
 #### 3.3.while, do while
  * while문은 다음과 같다. 괄호, 공백 및 중괄호의 배치에 유의하십시오.
  
  예제:
  
  ```php
  <?php
while ($expr) {
    // structure body
}
  ```
  마찬가지로 do while 구문은 다음과 같습니다. 괄호, 공백 및 중괄호의 배치에 유의하십시오.
  
  ```php
  <?php
do {
    // structure body;
} while ($expr);
  ```
 #### 3.4.for
  * for문 은 다음과 같습니다. 괄호, 공백 및 중괄호의 배치에 유의하십시오.
  ```php
  <?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
  ```
 #### 3.5.foreach
  * foreach문 은 다음과 같습니다. 괄호, 공백 및 중괄호의 배치에 유의하십시오.
  ```php
  <?php
foreach ($iterable as $key => $value) {
    // foreach body
}
  ```
 #### 3.6.try, catch
  * try catch 문은 다음과 같습니다. 괄호, 공백 및 중괄호의 배치에 유의하십시오.
  ```php
  <?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
  ```
### 4.Closures
 클로저는 function 구문 뒤의 공백과 use 구문 앞뒤 공백으로 선언해야합니다 (필수사항). 여는 중괄호는 반드시 같은 줄에 있어야하며 닫는 중괄호는 반드시 그 다음 줄에 있어야합니다. 인수 목록이나 변수 목록의 여는 괄호 다음에 공백이 있어서는 안되며 인수 목록이나 변수 목록의 닫는 괄호 앞에 공백이 있어서는 안됩니다. 인수 목록과 변수 목록에는 각 쉼표 앞에 공백이 있어서는 안되며 각 쉼표 뒤에 하나의 공백이 있어야합니다. 기본값을 가진 클로저 인수는 인수 목록의 끝에 와야합니다 (필수).

클로저 선언은 다음과 같습니다. 괄호, 쉼표, 공백 및 중괄호의 배치에 유의하십시오.

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```
인수 목록과 변수 목록은 여러 행에 걸쳐 나뉘어 질 수 있습니다 (각 행은 한 번 들여 쓰기됩니다). 그렇게 할 때 목록의 첫 번째 항목은 다음 줄에 있어야하며 한 줄에 하나의 인수 또는 변수 만 있어야합니다.

끝리스트 (인수 또는 변수의 여부)가 여러 줄로 나뉘어 질 때 닫는 괄호와 여는 중괄호는 한 줄의 공백을 사용하여 각각의 줄에 함께 있어야합니다 (MUST).

다음은 인수 목록이 있거나없는 클로저의 예와 여러 줄에 걸쳐있는 변수 목록입니다.
```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
    // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
    // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // body
};
```
형식 지정 규칙은 함수 또는 메소드 호출에서 클로저가 직접 인수로 사용될 때도 적용됩니다.
```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```
### 5.Conclusion
 * 전역 변수 및 전역 상수 선언
 * 함수 선언
 * 운영자 및 과제
 * 라인 간 정렬
 * 주석 및 문서 블록
 * 클래스 이름 접두사 및 접미사
 * 모범 사례
 
[🔝 목차로 돌아가기](#contents) 
### **PSR-3(Basic Coding Standard)**

[🔝 목차로 돌아가기](#contents)
### **PSR-4(Basic Coding Standard)**






### **단일 책임 원칙**

클래스와 메서드는 하나의 책임만 있어야 합니다.

나쁜 예:

```php
public function getFullNameAttribute()
{
    if (auth()->user() && auth()->user()->hasRole('client') && auth()->user()->isVerified()) {
        return 'Mr. ' . $this->first_name . ' ' . $this->middle_name . ' ' . $this->last_name;
    } else {
        return $this->first_name[0] . '. ' . $this->last_name;
    }
}
```

좋은 예:

```php
public function getFullNameAttribute()
{
    return $this->isVerifiedClient() ? $this->getFullNameLong() : $this->getFullNameShort();
}

public function isVerifiedClient()
{
    return auth()->user() && auth()->user()->hasRole('client') && auth()->user()->isVerified();
}

public function getFullNameLong()
{
    return 'Mr. ' . $this->first_name . ' ' . $this->middle_name . ' ' . $this->last_name;
}

public function getFullNameShort()
{
    return $this->first_name[0] . '. ' . $this->last_name;
}
```

[🔝 목차로 돌아가기](#contents)

### **모델은 무겁게, 컨트롤러는 가볍게**

DB와 관련된 로직은 Eloquent 모델이나 Repository 클래스에 작성되어야 합니다. 

나쁜 예:

```php
public function index()
{
    $clients = Client::verified()
        ->with(['orders' => function ($q) {
            $q->where('created_at', '>', Carbon::today()->subWeek());
        }])
        ->get();

    return view('index', ['clients' => $clients]);
}
```

좋은 예:

```php
public function index()
{
    return view('index', ['clients' => $this->client->getWithNewOrders()]);
}

class Client extends Model
{
    public function getWithNewOrders()
    {
        return $this->verified()
            ->with(['orders' => function ($q) {
                $q->where('created_at', '>', Carbon::today()->subWeek());
            }])
            ->get();
    }
}
```

[🔝 목차로 돌아가기](#contents)

### **Validation-유효성 검사**

유효성 검사 로직을 컨트롤러에서 Request 클래스로 옮깁니다.

나쁜 예:

```php
public function store(Request $request)
{
    $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
        'publish_at' => 'nullable|date',
    ]);

    ....
}
```

좋은 예:

```php
public function store(PostRequest $request)
{    
    ....
}

class PostRequest extends Request
{
    public function rules()
    {
        return [
            'title' => 'required|unique:posts|max:255',
            'body' => 'required',
            'publish_at' => 'nullable|date',
        ];
    }
}
```

[🔝 목차로 돌아가기](#contents)

### **비즈니스 로직은 서비스 클래스에 있어야 합니다.**

컨트롤러는 하나의 책임만 가지기 때문에 비즈니스 로직은 서비스 클래스에 있어야 합니다.


나쁜 예:

```php
public function store(Request $request)
{
    if ($request->hasFile('image')) {
        $request->file('image')->move(public_path('images') . 'temp');
    }
    
    ....
}
```

좋은 예:

```php
public function store(Request $request)
{
    $this->articleService->handleUploadedImage($request->file('image'));

    ....
}

class ArticleService
{
    public function handleUploadedImage($image)
    {
        if (!is_null($image)) {
            $image->move(public_path('images') . 'temp');
        }
    }
}
```

[🔝 목차로 돌아가기](#contents)

### **중복 배제(Don't repeat yourself)**

코드를 재사용합니다. 단일 책임 원칙뿐만 아니라 블레이드 템플릿, Eloquent 스코프 등은 코드의 중복을 피할 수 있도록 도와줍니다.

나쁜 예:

```php
public function getActive()
{
    return $this->where('verified', 1)->whereNotNull('deleted_at')->get();
}

public function getArticles()
{
    return $this->whereHas('user', function ($q) {
            $q->where('verified', 1)->whereNotNull('deleted_at');
        })->get();
}
```

좋은 예:

```php
public function scopeActive($q)
{
    return $q->where('verified', 1)->whereNotNull('deleted_at');
}

public function getActive()
{
    return $this->active()->get();
}

public function getArticles()
{
    return $this->whereHas('user', function ($q) {
            $q->active();
        })->get();
}
```

[🔝 목차로 돌아가기](#contents)

### **Query Builder, raw SQL 쿼리보다 Eloquent를 사용하는 것이 좋습니다.**

Eloquent를 사용하면 읽기 쉽고 유지 보수할 수 있는 코드를 작성할 수 있습니다. Eloquent는 소프트 삭제, 이벤트, 스코프 등 좋은 기능이 있습니다.

나쁜 예:


```sql
SELECT *
FROM `articles`
WHERE EXISTS (SELECT *
              FROM `users`
              WHERE `articles`.`user_id` = `users`.`id`
              AND EXISTS (SELECT *
                          FROM `profiles`
                          WHERE `profiles`.`user_id` = `users`.`id`) 
              AND `users`.`deleted_at` IS NULL)
AND `verified` = '1'
AND `active` = '1'
ORDER BY `created_at` DESC
```

좋은 예:

```php
Article::has('user.profile')->verified()->latest()->get();
```

[🔝 목차로 돌아가기](#contents)

### **Mass assignment-대량 할당**

나쁜 예:

```php
$article = new Article;
$article->title = $request->title;
$article->content = $request->content;
$article->verified = $request->verified;
// Add category to article
$article->category_id = $category->id;
$article->save();
```

좋은 예:

```php
$category->article()->create($request->all());
```

[🔝 목차로 돌아가기](#contents)

### **블레이드 템플릿에서 쿼리를 실행하지 않습니다. 그리고 즉시 로딩을 사용합니다.(N + 1 문제)**

나쁜예 (유저 전체를 가져오는 쿼리(1번) + 해당 유저의 프로필을 가져오는 쿼리(100번) = 101번 실행):

```php
@foreach (User::all() as $user)
    {{ $user->profile->name }}
@endforeach
```

좋은 예 (유저 전체를 가져오는 쿼리(1번) + 해당 유저의 프로필을 가져오는 쿼리(1번) = 2번 실행):

```php
$users = User::with('profile')->get();

...

@foreach ($users as $user)
    {{ $user->profile->name }}
@endforeach
```

[🔝 목차로 돌아가기](#contents)

### **코드에 주석을 작성합니다. 하지만 주석보다 의미있는 메서드 이름과 변수 이름을 사용하는 것이 더 좋습니다.**

나쁜 예:

```php
if (count((array) $builder->getQuery()->joins) > 0)
```

조금 더 나은 예:

```php
// Determine if there are any joins.
if (count((array) $builder->getQuery()->joins) > 0)
```

좋은 예:

```php
if ($this->hasJoins())
```

[🔝 목차로 돌아가기](#contents)

### **블레이드 템플릿에 JS와 CSS를 작성하지 않고 PHP 클래스에 HTML을 작성하지 않습니다.**

나쁜 예:

```php
let article = `{{ json_encode($article) }}`;
```

조금 더 나은 예:

```php
<input id="article" type="hidden" value="{{ json_encode($article) }}">

Or

<button class="js-fav-article" data-article="{{ json_encode($article) }}">{{ $article->name }}<button>
```

자바스크립트 파일:

```php
let article = $('#article').val();
```

The best way is to use specialized PHP to JS package to transfer the data.

[🔝 목차로 돌아가기](#contents)

### **코드에 텍스트로 작성하지 않고, 설정 파일, 언어 파일, 상수 등을 사용합니다.**

나쁜 예:

```php
public function isNormal()
{
    return $article->type === 'normal';
}

return back()->with('message', 'Your article has been added!');
```

좋은 예:

```php
public function isNormal()
{
    return $article->type === Article::TYPE_NORMAL;
}

return back()->with('message', __('app.article_added'));
```

[🔝 목차로 돌아가기](#contents)

### **라라벨 커뮤니티에서 수용하는 표준 라라벨 도구를 사용합니다.**

써드파티 패키지 및 도구 대신 내장되어있는 라라벨 기능과 커뮤니티 패키지를 사용합니다. 프로젝트에 참여하게 되는 개발자는 새로운 도구에 대해 학습을 해야합니다. 또한 써드파티 패키지나 도구를 사용할 때 라라벨 커뮤니티의 도움을 받을 수 있는 기회가 줄어듭니다. 

Task | Standard tools | 3rd party tools
------------ | ------------- | -------------
Authorization | Policies | Entrust, Sentinel and other packages
Compiling assets | Laravel Mix | Grunt, Gulp, 3rd party packages
Development Environment | Homestead | Docker
Deployment | Laravel Forge | Deployer and other solutions
Unit testing | PHPUnit, Mockery | Phpspec
Browser testing | Laravel Dusk | Codeception
DB | Eloquent | SQL, Doctrine
Templates | Blade | Twig
Working with data | Laravel collections | Arrays
Form validation | Request classes | 3rd party packages, validation in controller
Authentication | Built-in | 3rd party packages, your own solution
API authentication | Laravel Passport | 3rd party JWT and OAuth packages
Creating API | Built-in | Dingo API and similar packages
Working with DB structure | Migrations | Working with DB structure directly
Localization | Built-in | 3rd party packages
Realtime user interfaces | Laravel Echo, Pusher | 3rd party packages and working with WebSockets directly
Generating testing data | Seeder classes, Model Factories, Faker | Creating testing data manually
Task scheduling | Laravel Task Scheduler | Scripts and 3rd party packages
DB | MySQL, PostgreSQL, SQLite, SQL Server | MongoDB

[🔝 목차로 돌아가기](#contents)

### **라라벨 네이밍 규칙을 따릅니다.**

 [PSR 표준](http://www.php-fig.org/psr/psr-2/)을 따릅니다.
 
또한 라라벨 커뮤니티에서 수용하고 있는 네이밍 규칙을 따릅니다:

What | How | Good | Bad
------------ | ------------- | ------------- | -------------
Controller | singular | ArticleController | ~~ArticlesController~~
Route | plural | articles/1 | ~~article/1~~
Named route | snake_case with dot notation | users.show_active | ~~users.show-active, show-active-users~~
Model | singular | User | ~~Users~~
hasOne or belongsTo relationship | singular | articleComment | ~~articleComments, article_comment~~
All other relationships | plural | articleComments | ~~articleComment, article_comments~~
Table | plural | article_comments | ~~article_comment, articleComments~~
Pivot table | singular model names in alphabetical order | article_user | ~~user_article, articles_users~~
Table column | snake_case without model name | meta_title | ~~MetaTitle; article_meta_title~~
Model property | snake_case | $model->created_at | ~~$model->createdAt~~
Foreign key | singular model name with _id suffix | article_id | ~~ArticleId, id_article, articles_id~~
Primary key | - | id | ~~custom_id~~
Migration | - | 2017_01_01_000000_create_articles_table | ~~2017_01_01_000000_articles~~
Method | camelCase | getAll | ~~get_all~~
Method in resource controller | [table](https://laravel.com/docs/master/controllers#resource-controllers) | store | ~~saveArticle~~
Method in test class | camelCase | testGuestCannotSeeArticle | ~~test_guest_cannot_see_article~~
Variable | camelCase | $articlesWithAuthor | ~~$articles_with_author~~
Collection | descriptive, plural | $activeUsers = User::active()->get() | ~~$active, $data~~
Object | descriptive, singular | $activeUser = User::active()->first() | ~~$users, $obj~~
Config and language files index | snake_case | articles_enabled | ~~ArticlesEnabled; articles-enabled~~
View | snake_case | show_filtered.blade.php | ~~showFiltered.blade.php, show-filtered.blade.php~~
Config | snake_case | google_calendar.php | ~~googleCalendar.php, google-calendar.php~~
Contract (interface) | adjective or noun | Authenticatable | ~~AuthenticationInterface, IAuthentication~~
Trait | adjective | Notifiable | ~~NotificationTrait~~

[🔝 목차로 돌아가기](#contents)

### **될 수 있으면 짧고 읽기 쉬운 문법을 사용합니다.**

나쁜 예:

```php
$request->session()->get('cart');
$request->input('name');
```

좋은 예:

```php
session('cart');
$request->name;
```

더 많은 예시:

Common syntax | Shorter and more readable syntax
------------ | -------------
`Session::get('cart')` | `session('cart')`
`$request->session()->get('cart')` | `session('cart')`
`Session::put('cart', $data)` | `session(['cart' => $data])`
`$request->input('name'), Request::get('name')` | `$request->name, request('name')`
`return Redirect::back()` | `return back()`
`is_null($object->relation) ? $object->relation->id : null }` | `optional($object->relation)->id`
`return view('index')->with('title', $title)->with('client', $client)` | `return view('index', compact('title', 'client'))`
`$request->has('value') ? $request->value : 'default';` | `$request->get('value', 'default')`
`Carbon::now(), Carbon::today()` | `now(), today()`
`App::make('Class')` | `app('Class')`
`->where('column', '=', 1)` | `->where('column', 1)`
`->orderBy('created_at', 'desc')` | `->latest()`
`->orderBy('age', 'desc')` | `->latest('age')`
`->orderBy('created_at', 'asc')` | `->oldest()`
`->select('id', 'name')->get()` | `->get(['id', 'name'])`
`->first()->name` | `->value('name')`

[🔝 목차로 돌아가기](#contents)

### **new Class 대신 IoC 컨테이너 또는 파사드를 사용합니다.**

new Class 문법은 클래스 간의 결합도를 높이고 테스트를 복잡하게 만듭니다. new Class 문법 대신에 IoC 컨테이너 또는 파사드를 사용합니다.

나쁜 예:

```php
$user = new User;
$user->create($request->all());
```

좋은 예:

```php
public function __construct(User $user)
{
    $this->user = $user;
}

....

$this->user->create($request->all());
```

[🔝 목차로 돌아가기](#contents)

### **`.env` 파일에서 직접 데이터를 가져오지 않습니다.**

데이터를 설정 파일에 전달한 다음 `config()` helper 함수를 통해 애플리케이션에서 데이터를 사용합니다.

나쁜 예:

```php
$apiKey = env('API_KEY');
```

좋은 예:

```php
// config/api.php
'key' => env('API_KEY'),

// Use the data
$apiKey = config('api.key');
```

[🔝 목차로 돌아가기](#contents)

### **날짜를 표준 형식으로 저장합니다. accessors(get), mutators(set)을 사용해 날짜 형식을 수정합니다.**

나쁜 예:

```php
{{ Carbon::createFromFormat('Y-d-m H-i', $object->ordered_at)->toDateString() }}
{{ Carbon::createFromFormat('Y-d-m H-i', $object->ordered_at)->format('m-d') }}
```

좋은 예:

```php
// Model
protected $dates = ['ordered_at', 'created_at', 'updated_at']
public function getSomeDateAttribute($date)
{
    return $date->format('m-d');
}

// View
{{ $object->ordered_at->toDateString() }}
{{ $object->ordered_at->some_date }}
```

[🔝 목차로 돌아가기](#contents)

### **또 다른 좋은 사례**

라우트 파일에 로직을 작성하지 않습니다.

블레이드 템플릿에 바닐라 PHP의 사용을 최소화합니다.

[🔝 목차로 돌아가기](#contents)
