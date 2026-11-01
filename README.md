import java.util.Scanner;

// الصنف Point: يمثل نقطة في المستوى (فيه x و y)
class Point {

    // إحداثيات النقطة
    double x;
    double y;

    // المُنشئ: يعطي القيم الأولى للنقطة عند إنشائها (التهيئة)
    Point(double x, double y) {
        this.x = x;   // this.x = خاصية الكائن، x = القيمة المرسلة
        this.y = y;
    }

    // دالة الإزاحة: تحرّك النقطة بـ dx على المحور x و dy على المحور y
    void deplacer(double dx, double dy) {
        x = x + dx;
        y = y + dy;
    }

    // دالة المسافة: تحسب المسافة بين هذه النقطة ونقطة أخرى
    // القانون: racine((x2-x1)² + (y2-y1)²)
    double distance(Point autre) {
        double difX = autre.x - x;
        double difY = autre.y - y;
        return Math.sqrt(difX * difX + difY * difY);
    }

    // دالة العرض: تكتب النقطة على الشاشة
    void afficher() {
        System.out.println("(" + x + ", " + y + ")");
    }
}

// الصنف الرئيسي: منه يبدأ البرنامج
public class TP01poo {

    public static void main(String[] args) {

        // Scanner: لقراءة القيم التي يكتبها المستخدم
        Scanner sc = new Scanner(System.in);

        // 1) تهيئة النقطتين: نقرأ الإحداثيات وننشئ كائنين
        System.out.print("P1 (x y) : ");
        double x1 = sc.nextDouble();
        double y1 = sc.nextDouble();
        Point p1 = new Point(x1, y1);

        System.out.print("P2 (x y) : ");
        double x2 = sc.nextDouble();
        double y2 = sc.nextDouble();
        Point p2 = new Point(x2, y2);

        System.out.print("P1 = ");
        p1.afficher();
        System.out.print("P2 = ");
        p2.afficher();

        // 2) إزاحة P1: نقرأ dx و dy ثم نستدعي الدالة
        System.out.print("Deplacement de P1 (dx dy) : ");
        double dx = sc.nextDouble();
        double dy = sc.nextDouble();
        p1.deplacer(dx, dy);

        System.out.print("P1 apres deplacement = ");
        p1.afficher();

        // 3) حساب المسافة بين P1 و P2
        double d = p1.distance(p2);
        System.out.println("Distance P1-P2 = " + d);

        sc.close();
    }
}
