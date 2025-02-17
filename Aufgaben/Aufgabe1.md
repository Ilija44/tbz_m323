
# Aufgabe 1 - imperativ vs. deklarativ

## Imperativer Stil mit Anpassung
```java
public static int calculateScore(String word) {
    int score = 0;
    for (char c : word.toCharArray()) {
        if (c != 'a') {
            score++;
        }
    }
    return score;
}
```

## Deklarativer Stil mit Anpassung
```java
public static int wordScore(String word) {
    return (int) word.chars().filter(c -> c != 'a').count();
}
```
# Aufgabe 2 - Shopping Cart Funktion

## Imperative Umsetzung
```java
class ShoppingCart {
    private List<String> items = new ArrayList<>();
    private boolean bookAdded = false;

    public void addItem(String item) {
        items.add(item);
        if (item.equalsIgnoreCase("book")) {
            bookAdded = true;
        }
    }

    public void removeItem(String item) {
        items.remove(item);
        if (item.equalsIgnoreCase("book") && !items.contains("book")) {
            bookAdded = false;
        }
    }

    public List<String> getItems() {
        return items;
    }

    public double getDiscount() {
        return bookAdded ? 5.0 : 0.0;
    }
}
```
## Funktionale Umsetzung
```java
import java.util.List;

public class ShoppingCartFunctional {
    public static double getDiscountPercentage(List<String> cart) {
        return cart.contains("book") ? 5.0 : 0.0;
    }
}
```
# Aufgabe 3 - TipCalculator

```java
import java.util.List;

public class TipCalculator {
    public static int calculateTip(List<String> names) {
        if (names.isEmpty()) {
            return 0;
        }
        return names.size() > 5 ? 20 : 10;
    }
}
```
