# 4.AAI-ReadKbd
Listing 4 AAI-ReadKbd/ReadKbd.java Page 17

# Section 4. Quick introduction to I/O  

We will show here, how data can be read from the console (standard input by default is connected to the keyboard) and from a graphical window. First, let us consider a console. The simplest way to read from the standard input is by creating an object of class Scanner, as shown in the example below. The import statements at the beginning are not necessary, but without them, one would have to use full, qualified names of classes, e.g., java.util.Scanner instead of just Scanner.  

There is a little problem with reading values of floating-point types: whether to use a dot or a comma as the decimal separator. This depends on the locale; for example, for Polish locale a comma should be used, for the American one - a dot. The current locale may be changed, as explained below in comments.  

## Listing 4 AAI-ReadKbd/ReadKbd.java  

```java
import java.util.Scanner;
import java.util.Locale;  // see below

public class ReadKbd {
    public static void main(String[] args) {

        // If locale is Polish, floating point numbers
        // have to be entered with  c o m m a  as the
        // decimal separator. Locale can be changed to,
        // e.g., American, by uncommenting the line below:
        //    Locale.setDefault(Locale.US);
        // (then the dot is is used as decimal separator).
        // When reading data, any nonempty sequence of
        // white characters is treated as a separator.

        //Locale.setDefault(Locale.US);
        Scanner scan = new Scanner(System.in);

        System.out.println("Enter an int, a string " +
                           "and two double's");
        int    k = scan.nextInt();
        String s = scan.next();
        double x = scan.nextDouble();
        double y = scan.nextDouble();
                // scan.close(); // don't close if reading from System.in
        System.out.println("\nEntered data:\n\nint     = " +
                k + "\nString  = " + s  + "\ndouble1 = " +
                x + "\ndouble2 = " + y + "\n");
    }
```
We used here `nextInt` (to read an `int`), `nextDouble` (to read a `double`), and `next` (to read a `String`): there are analogous functions `nextByte`, `nextShort`, `nextLong`, `nextBigInteger`, `nextFloat`, `nextBigDecimal`, and `nextBoolean`.  

> [!NOTE]
> when all ata has been read, the scanner should be closed (by invoking scan.close(), as shown in the example).  

In order to read data from a graphical widget, or to display a message (`string`), one can use static functions from class `JOptionPane`, as shown below (the first argument of these functions is null for reasons we will learn about later). Note that showInputDi-
alog returns a string (strictly speaking the reference to a string); if we know that this
string represents a number and we want this number as an int or a double, we have
to parse this string to get numbers using Integer.parseInt, or Double.parseDouble):

