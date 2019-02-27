# 1 javaの基本

1. パッケージ宣言に関するルール
- 1.1 必ずソースコードの先頭行に記述する
- 1.2 前に記述できるのはコメントだけである
- 1.3 パッケージ名.クラス名　→　完全修飾クラス名　→　名前区間を提供し、名前の衝突を避ける
- 1.4 パッケージ単位でアクセス制御する
   例　package aa
      class test{//any code}
   → 外部パッケージからアクセスできない
- 1.5 パッケージはディレクトリ構造とマッピング
- 1.6 クラスは必ずパッケージに所属する　ディフォルトはdefault 無名パッケージ
- 1.7 無名パッケージに属するクラスは同じ無名パッケージに属するクラスからしかあくせすできない

2. インポート
- 2.1 import static ○  static import ☓　　　
- 2.2 メソッドのstatic インポート宣言では、メソッド名にかっこ「()」や引数を付けない。
- 2.3 インポートしたクラスに、インポートされたメソッドやフィールドと同名のものがあった場合,そのインポートは無視される
- 2.4 java コマンドでのクラス実行時に指定する起動パラメータはString配列型オブジェクトに格納されるため、1番目が配列型変数args[0]、2番目がargs[1]となる

3. java コマンドの構文

- 3.1 java 完全修飾クラス名　引数1　引数2
- 3.2 引数1,引数2は起動パラメータやコマンドライン引数と呼ぶ

# 2 javaのデータ型の操作

1. javaでは数値を10進数のほかに、2進数、8進数、16進数のリテラルで表示でき、それぞれ、0b,0,0xで始め

2. リテラルの先頭と末尾には記述できない

- 2.1　記号の前後には記述できない

- 2.2　利用できる記号は、小数点を表すドット「.」long型やfloat型リテラルを表す[L]や[F]、2進数を表す[0b] 16進数を表す[0x]

3. char型の変数には、ダブルクォーテーション「"]で括った文字列りてらるは代入できません。

- 代入できるのは、シングルクォーテーション[']で括った文字列リテラル、もしくは数値のみ、シングルクォーテーション、ダブルクォーテーションを間違えないように

- char型の変数に代入できるのは、0~65535までの数値だけ、符号つきの整数(負の値)は扱えない

- Unicodeの代入￥u30A2

4. 識別子に使える記号はアンダースコア「_」とドル[$]

5. 以下の識別子が使えない　!@#%&^()':;[/\\]

6. ガーベジコレクション、ガーベジコレクション

7. インスタンスの参照がなくなった時点で、カーベッジコレクションの対象となる

8. カーベッジコレクションのタイミングはjvmが決めます。gcメソッドは促すだけで保証はされない

# 3 演算子っと判定構造の使用

- 1.byteとshortは扱う範囲が狭いデータ型

- 2.byteとbooleanの互換性はない

- 3.**インクリメント**演算子「++」やデクリメント「--」演算子の前置と後置の違いによる演算子の動作順序は　重要ポイント

- 4.カッコやインクリメント、デクリメントが最優先である

- 4.1数学と同じで乗算や除算、剰余算が加算や減算より優先される

- 5 ネストした三項演算子は「？」と「：」が交互に現れ、最後だけ「：」で終わります

- 6 switch文のcase値として使用できる値　

  * 6.1　条件式に戻り値と同じ型か互換性がある型であること

　　* 6.2    定数であるか、コンパイル時に値を決めることができること

　　* 6.3    nullでないこと　

-　7 switch 文の条件式　

　　* 7.1 int型以下の整数型　と　そのラッパークラス

　　* 7.2 文字と文字列　

　　* 7.3 列挙型　eum 

　　　　

# 4 配列の作成と使用

1. new int[0] でもコンパイルエラーにならない

2. 配列宣言

   2.1　int[] a  int a[]

   2.2    int[]  a[]   int [] [] a  int a[] []

   2.3    int[] array[] []  int[] [] array[]

3. 要素の指定のとき、データ型変換は行わない、宣言したデータ型しか使えない

4. 2次元配列宣言　1次元の配列の要素数を先に記述しなければならない。

5. 配列インスタンス生成・初期化のとき

   5.1　int[] a = {2,3}  int[] a = new int[]{2,3}  int[] a = {} →　ok  

   int[] a = new int[2]{2,3} →　エラーになる　　int[] a ; a={2,3} →　エラーになる

   5.2   new と初期化演算子の両方を使って配列のインスタンス生成と初期化を同時に行う場合、要素数は自動算出されるため、大カッコ中に要素数は指定できない

   5.3　初期化演算子を使って、配列のインスタンス生成と初期化を同時に行う場合、変数の宣言と参照の代入も同時に行う。セミコロン「；」を使って変数宣言と配列のインスタンス生成のタイミングを分けることはできない

   

6. ```java
   public class Test {
   
       public static void main(String[] args){
           String[][] array = {{"A","B"},null,{"C","D","E"}};
           int total = 0;
           for(String[] tmp:array){
               total += tmp.length;
           }
       }
   }
   ```

```java
// public interface A{}

// public abstract class B implements A{}

// public class c extends B{}

// public class d extends C{}



public class Test {

    public static void main(String[] args){
          A{}  array = {newC(),null,new D()};
          Object [] objArray = array;
    }
}
```

# 5 ループ構造と使用

1 while文やdo-while文では、中カッコを省略した場合、次の1文だけが繰り返し対象となる

2.do while 文で中カッコを省略した場合には、doとwhileの間には1文のみを記述できる　2文以上記述した場合には、コンパイルエラーが発生する

3.for文の初期化文では　同じ型の変数を複数宣言できるが、異なる変数を同時に宣言できない。コンパイルエラーになる

４for文条件文を複数記述する場合は論理演算子を使うカンマを使うとコンパイルエラーになる

 5 二重ループ

 6 for文の条件式を省略するできるが、breakがないと無限ループになる

　6.1 条件式　true の場合　無限ループ　

 7  contiuneは 以降の処理をスキップしてループの条件判定に戻る

 

```java
public static void main(String[] args){
    int total = 0;
    a: for(int i=0 ;i<5;i++){
        b: for(int j=0;j<5;j++){
            if(i%2==0)continue a;    
            if(3 < j)break b;
            total += j;
        }        
    }
}
```







# 6 メソッドとカプセル化び操作

```java
public static void main(String[] args){
        
    Sample s = new Sample();
     ? result = s.divide(10,2);
     System.out.println(result);
    
}


public class Sample{
    float divide(int a ,int b){
        return (float)a/(float)b;
    }
}
```



6

```java
public void method(int num){
        if(num<0)return;
        System.out.println("A");
        return;
        System.out.println("B");
}
```

6.1 return 文の後ろ処理は実行できない、もしreturn文を実行したあとに何らかの処理をするようなコードを記述するとコンパイルエラーになる



7

```java
public static void main(String[] args){
    
    Sample.num = 10;
    Sample s = new Sample();
    Sample s2 = new Sample();
    s.num += 10;
    s2.num = 30;
    System.out.println(Sample.num);
}

public class Sample{
    static int num = 0;
}
```

static なフィールドは「クラス名.フィールド名」、もしくはインスタンスの作成後であれば、「変数名.フィールド名」のどちらでもアクセスできる



static ではメソッドからは,staticなフィールドにアクセスできる      ○

static ではないメソッドからは、staticなメソッドを呼び出せない　☓



public void sample {

​	{ 

​		初期化ブロックで行う共通の処理

​	}

}



コンストラクタうちから、オーバーロードされたほかのコンストラクタを呼び出すにはthisを使う



```java
package other;
import ex18.Parent

public class Chile extends Parent {

    public static void main(String[] args){
        System.out.println(num);

    }

    
    package ex18;
    
    public class Parent{
        int num = 10;
    }

}
```





```java
package other;
public class Book{
    
    private String isbn;
    public  void setIsbn(String isbn){
        this.isbn = isbn;
    }
    
    protected void printInfo(){
        System.out.println(isbn);
    }
    
}


package ex19;
import other.Book;
public class StoryBook extends Book(){}

package ex19;
public class Main(){
    public static void main(String[] args){
        StoryBook story = new StoryBook();
        story.setIsbn("======");
        story.printInfo();
         }
     }
```





# 7 継承の操作

```java
abstract class AbstractSample{
    public void sample(){
        System.out.println("A");
        test();
        System.out.println("B");
    }
    protected void test(){}
}

class ConcreteSample extends AbstractSample{
    protected void test(){
        System.out.println("B");
    }
}

public static void main(String[] args){
    AbstractSample s = new AbstractSample() {
        s.sample();
    }
}
```



１。オーバーライド３つルール

　　１．１シグニチャが同じであること

　　１．２戻り値は同じか、サブクラスであること

　　１・３アクセス修飾子は同じか、よりゆるいもの



```java
class A{
    String val = "A";
    void print(){
        System.out.println(val);
    }
}

class B extends A {
    String val = "B";
}


public class  Main{
    public static void main(String[] args){
        A a = new A();
        A b = new B();
        System.out.println(a.val);
        System.out.println(b.val);
        
        a.print();
        b.print();
    }
}
```





```java
public interface A {
    
}

public class B implements  A{}

public class C extends B{
    
}
public class  D{}

public class  Main{
    public static void main(String [] args){
        A[] array ={
                new B(),
                new C(),
                new A(),
                new D()
        };
    }
        
}
```





```java
class A {
    void hello(){
        System.out.println("A");
    }
}


class B extends A{
    void hello(){
        System.out.println("B");
    }
}

public class  Main{
    public static void main(String[] args){
        A a = new A();
        B b = (B)a;
        b.hello();
    }
}
```





```java
class Parent{
    String name;
    String getName(){
        return this.name;
    }
    
}

public class Child extends Parent{
    String name;
}

public class  Main{
    public static void main(String[] args){
        Child child = new Child();
        child.name = "smaple";
        System.out.println(child.getName());
    }
}
```





```java
class A{
    public A(){
        System.out.println("A");
    }
}

class B extends A{
    public B(){
        System.out.println("B");
    }
}
public class  Main{
    public static void main(String[] args){
        A a = new B();
    }
}
```



```java
class Parent{

    public Parent(){
        System.out.println("A");
    }
    
    public Parent(String val){
        this();
        System.out.println(val);
    }
}


public class Child extends Parent{
    public Child(){
        super("B");
        System.out.println("C");
    }
    
    public Child(String val){
        this();
        System.out.println(val);
    }
}

public class  Main{
    public static void main(String[] args){
        new Child("D");
    }
}
```





# 8 例外の処理

OutOfMemoryError



VirtualMachineError



InternalError



NoClassDefFoundError



Exception InInitializerError



NullPointerException



stackOverflowError





# 9 java APIの主要なクラス操作

StringBuilderクラス

StringBuilderクラスのメソッド

1.str.trim()

2.str.charAt()

3.str.indexOf()

4.str.substring()

5.str.startsWitch()

6.str.split()

7 Stringbuilder.append()

8.Stringbuilder.delete()

9.Stringbuilder.deleteCharAt()

10.Stringbuilder.reverse()

11.Stringbuilder.replace()

12.str.concat()

Stringbuilderディフォルトで16文字分のバッファを持っている



ラムダ式

Predicateインタフェース

LocalDateクラス、LocalTimeクラス、各クラスのメソッド

localDate.until
localDate.minuns



Durationクラス、Durationクラスのメソッド

Periodクラス,Periodクラスのメソッド

DataTimeFormatterクラス、formatメソッド

ArrayListクラス、ArrayListクラスのメソッド

```java
1
public class Main{
    public static void main(String[] args) {
        LocalTime localTime = LocalTime.of(0,1,2);
        localTime.plusHours(12);
        System.out.println(time);
    }
}

2
public class Sample{
    public static void main(String[] args){
        LocalDateTime start =LocalTime.of(2015,1,1,0,0);
        LocalDateTime end = LocalTime.of(2015,1,2,1,0,0);
        Duration d = Duration.between(start,end);
        System.out.println(d.toHours());
    }
}
3
public class Main{
    public static void main(String[] args) {
        LocalDate now = LocalDate.now();
        LocalDate target = now.plusDays(10);

        System.out.println(x.getDays());
        //画面に10と表示したい
    }
}

4
public class Sample{
    public static void main(String[] args){
        LocalDateTime time =LocalTime.of(2015,1,1,0,0);
        String str = time.format();
        System.out.println(str);
        //2015-08-31T00:00:00と表示したい
        //DateTimeFormatter.BASIC_ISO_DATE
	//DateTimeFormatter.ISO_ZONED_DATE_TIME
	//DateTimeFormatter.ISO_INSTANT
	//DateTimeFormatter.ISO_DATE_TIME
    }
}

5
public class Sample{
    public static void main(String[] args){
        LocalDate a = LocalDate.of(2015,0,1);
        LocalDate b = LocalDate.parse("2015-01-01");
        System.out.println(a.equals(b));
        
        
        
    }
}

```

ラムダ式

```java
6


public class Main{
    public static void main(String[] args){
        
        Function f = (name)-> "hello." + name;
        // Function f = (name) ->{return "hello." + name;}
       	// Function f = (name) ->{ "hello." + name;}
	// Function f = name ->{return "hello." + name;}
	// Function f = (name) ->return "hello." + name;
        System.out.println(f.test("Lambda"));
    }
    
    private static interface Function{
        String test(String name);
    }
}

```
１．メソッド内で宣言したローカル変数と同じ名前の変数をラムダ式の引数として使うことができない
２．ラムダ式外で宣言されたローカル変数にラムダ式内からアクセスするには、自質にfinalな変数でなければいけない


7ArrayList 

```java
1
public class Sample{
    public static void main(String[] args){

        ArrayList list = new ArrayList<>();
        
        list.add("A");
        list.add(10);
        list.add("B");
        for(Object obj: list){
            System.out.println(obj);
        }

    }
}
2
public class Sample{
    public static void main(String[] args){

        ArrayList<String> list = new ArrayList<>();

        list.add("A");
        list.add(2,"B");
        list.add("C");
        list.add("D");


        for(String str:list){
            System.out.println(str);
        }

    }
}

3

public class Sample{
    public static void main(String[] args){

        ArrayList<String> list = new ArrayList<>();

        list.add("A");
        list.add(0,"B");
        list.add("C");
        list.add(1,"D");


        for(String str:list){
            System.out.println(str);
        }

    }
}


4

public class Item{
    private String name;
    private int price;
    public Item(String name,int price){
        this.name = name;
        this.price = price;
    }

    public boolean equals(Object obj){
        if(obj instanceof Item){
            Item tmp = (Item)obj;
            if(tmp.name.equals(this.name));
                return true;
        }
        return false;
    }
    
    public String getName(){
        return name;
        
    }
}

public class Main{
    public  static void main(String [] args){
        ArrayList<Item> list = new ArrayList<>();
        list.add(new Item("A",100));
        list.add(new Item("B",200));
        list.add(new Item("C",300));
        list.add(new Item("A",100));
        list.remove(new Item("A",500));
        for (Item item:list){
            System.out.println(item.getName());
        }
    }
}


5


public class Main{
    public  static void main(String [] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");

        for (String str:list){
            if("B".equals(str)){
                list.remove(str);
            }else {
                System.out.println(str);
            }
        }
    }
}

6

public class Main{
    public  static void main(String [] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");
        list.add("D");
        list.add("E");
        for (String str:list){
            if("C".equals(str)){
                list.remove(str);
            }
        }
        for (String str:list){
            System.out.println(str);
        }
    }
}

7

public class Main{
    public  static void main(String [] args) {
        List<String> list = new ArrayList<>(
                Arrays.asList(new String[]{"A","B","C"})
        );
        
        list.removeIf(
                (String s)->{
                    return s.equals("B");
                }
        );
        
        System.out.println(list);
    }
}


```