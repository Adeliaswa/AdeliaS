import java.util.Scanner;

public class buah3ArrayMethod {
    public static void main(String[] args) {

        System.out.println("\nList kode buah dan harga per Kg: ");
        System.out.println("A. 10000\nB. 15000\nC. 20000");

        String[] kodeBuah = {"A", "B", "C"};
        int[] hargaPerKg = {10000, 15000, 20000};

        Scanner input = new Scanner(System.in);
        String kode;
        int berat;
        int totalHargaSemuaBuah = 0;
    
        while (true) {
            System.out.print("Masukkan kode buah atau ketik 'x' untuk selesai: ");
            kode = input.next().toUpperCase();

            if (kode.equalsIgnoreCase("X")) {
                break;
            }

            System.out.print("Masukkan berat buah yang dibeli (dalam kg): ");
            berat = input.nextInt();

            int harga = cariHarga(kode, kodeBuah, hargaPerKg);
            if (harga <= 0) {
                System.out.println("Kode buah tidak valid!");
            } else {
                int hargaTotal = harga*berat;
                totalHargaSemuaBuah += hargaTotal;
                System.out.println("Harga " + berat + " kg buah " + kode + ": Rp " + hargaTotal);
            }
        }

        System.out.println("Total harga semua buah yang dibeli: Rp " + totalHargaSemuaBuah);
        input.close();
    }

    public static int cariHarga(String kode, String[] kodeBuah, int[] hargaPerKg) {
        for (int i = 0; i < kodeBuah.length; i++) {
            if (kodeBuah[i].equalsIgnoreCase(kode)) {
                return hargaPerKg[i];
            }
        }
        return -1;
    }
}
