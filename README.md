import java.util.Scanner;

// Lớp cha: Giải phương trình bậc 1
class PhuongTrinhBac1 {
    protected double a, b;

    public PhuongTrinhBac1(double a, double b) {
        this.a = a;
        this.b = b;
    }

    // Giải phương trình bậc 1: ax + b = 0
    public void giai() {
        if (a == 0) {
            if (b == 0)
                System.out.println("Phương trình có vô số nghiệm.");
            else
                System.out.println("Phương trình vô nghiệm.");
        }
        else {
            double x = -b / a;
            System.out.println("Phương trình có nghiệm: x = " + x);
        }
    }
}

// Lớp con: Giải phương trình bậc 2 (kế thừa từ lớp bậc 1)
class PhuongTrinhBac2 extends PhuongTrinhBac1 {
    private double c;

    public PhuongTrinhBac2(double a, double b, double c) {
        super(a, b); // gọi constructor lớp cha
        this.c = c;
    }

    // Ghi đè phương thức giai() để xử lý bậc 2
    @Override
        public void giai() {
        if (a == 0) {
            System.out.println(" Vì a = 0 nên phương trình trở thành bậc 1:");
            super.giai(); // gọi lại hàm của lớp cha
        }
        else {
            double delta = b * b - 4 * a * c;

            if (delta < 0)
                System.out.println(" Phương trình vô nghiệm thực.");
            else if (delta == 0)
                System.out.println("Phương trình có nghiệm kép: x = " + (-b / (2 * a)));
            else {
                double x1 = (-b + Math.sqrt(delta)) / (2 * a);
                double x2 = (-b - Math.sqrt(delta)) / (2 * a);
                System.out.println(" Phương trình có 2 nghiệm phân biệt:");
                System.out.println("   x1 = " + x1);
                System.out.println("   x2 = " + x2);
            }
        }
    }
}

// Chương trình chính (Main)
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("===== CHƯƠNG TRÌNH GIẢI PHƯƠNG TRÌNH BẬC 2 =====");
        System.out.print("Nhập a: ");
        double a = sc.nextDouble();
        System.out.print("Nhập b: ");
        double b = sc.nextDouble();
        System.out.print("Nhập c: ");
        double c = sc.nextDouble();

        PhuongTrinhBac2 pt2 = new PhuongTrinhBac2(a, b, c);
        pt2.giai();

        System.out.println("===============================================");
        System.out.println("Cảm ơn bạn đã sử dụng chương trình của Minh!");
        sc.close();
    }
}
