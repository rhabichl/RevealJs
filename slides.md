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
}
```

---

## Unit Test für add()

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

* push auf main branch
* nutzt Linux Maschine
* Java Version 17

---
### Bedingung festlegen
```yaml
on:
  push:
```
---
### Plattform festlegen
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
```
---
### Umgebung bereit machen
```yaml
      - name: Checkout
        uses: actions/checkout@v3
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'adopt'
```
---
### Test ausführen
```yaml
        # build and test the programm
      - name: Test
        run: mvn --batch-mode --update-snapshots verify
```
--
## Zuckerl 
* Docker container
* Enviroment Variables

---
### Docker container
```yaml
version: '3.8'
services:
  database:
    container_name: ci-cd-test_postgres
    image: postgres:15.1-alpine
```
---
### start container
```yaml
...
- name: Start Docker-Container
  run: docker-compose up -d
...
```
---
### Enviroment Variables
```yaml
...
- name: Greet person
  run: echo "hello $NAME"
  env:
    NAME: Sengseis
...
```
