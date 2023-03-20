# GitHub Actions

--

## Typography

---

## Quotes

> Quotes are ~~hard~~ easy
> to write - but you can use `code`

--

## Beispiel   

---

## Zu testender Code 

```Java 
public class MathHelper {
    // adds two numbers and returns the sum
    public  static Integer add(int a, int b){
        return a + b;
    }
}`
```

---

## Unit Test für die Funktion add()

```Java
class MathHelperTest {
    @Test
    void add() {
        int a = 1;
        int b = 1;
        Assertions.assertEquals(a+b, MathHelper.add(a,b));
    }
}
```

---

## Workflow 

```yaml
on:
  push:
```
<!-- .element: class="fragment" data-fragment-index="2" -->
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
```
<!-- .element: class="fragment" data-fragment-index="2" -->
<!-- .element: class="fragment" data-fragment-index="3" -->
```yaml
        # set up testing-env
      - name: Checkout
        uses: actions/checkout@v3
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'adopt'
          cache: maven
```<!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .element: class="fragment" data-fragment-index="4" -->
```yaml
        # build and test the programm
      - name: Test
        run: mvn --batch-mode --update-snapshots verify
```
<!-- .element: class="fragment" data-fragment-index="4" -->

#### Private methods in Interfaces<!-- .element: class="fragment" data-fragment-index="2" -->

```java
interface Version {
    byte[] digits();
    default String text() { return text(digits()); }
    private String text(byte[] version) { … }
}
```
<!-- .element: class="fragment" data-fragment-index="2" -->

--
## Images

<span>To say it with
[Dilbert](https://dilbert.com/strip/1995-12-10):</span><!-- .element: class="decent x-small"-->

![](https://assets.amuniversal.com/0e1eaf909fcf012f2fe600163e41dd5b)
