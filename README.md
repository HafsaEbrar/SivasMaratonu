import java.util.HashMap;
import java.util.Map;

public class SivasMaratonu {

    public static void main(String[] args) {
        Map<String, Integer> dereceler = new HashMap<>();
        dereceler.put("kadir", 341);
        dereceler.put("gökhan", 273);
        dereceler.put("hakan", 278);
        dereceler.put("suzan", 329);
        dereceler.put("pınar", 445);
        dereceler.put("mehmet", 402);
        dereceler.put("ali", 388);
        dereceler.put("emel", 270);
        dereceler.put("fırat", 243);
        dereceler.put("james", 334);
        dereceler.put("jale", 412);
        dereceler.put("ersin", 393);
        dereceler.put("deniz", 299);
        dereceler.put("gözde", 343);
        dereceler.put("anıl", 317);
        dereceler.put("burak", 265);

        // İlk üç dereceyi alan öğrencileri yazdır
        ilkUcDereceyiYazdir(dereceler);

        // En düşük zamanı elde eden öğrenciyi yazdır
        int enDusukIndex = enDusukZamanaSahipKisi(dereceler);
        String enDusukKisi = getKeyByValue(dereceler, enDusukIndex);
        System.out.println("En düşük zaman: " + enDusukKisi + " - " + enDusukIndex);

        // İkinci en iyi koşucuyu bul
        int ikinciEnIyiIndex = ikinciEnIyiKosucuyuBul(dereceler, enDusukIndex);
        String ikinciEnIyiKisi = getKeyByValue(dereceler, ikinciEnIyiIndex);
        System.out.println("İkinci en iyi zaman: " + ikinciEnIyiKisi + " - " + ikinciEnIyiIndex);

        // Sınıflandırmayı yap ve sonuçları yazdır
        siniflandirmayiYap(dereceler);
    }

    public static void ilkUcDereceyiYazdir(Map<String, Integer> dereceler) {
        System.out.println("İlk üç dereceyi alan öğrenciler:");
        int count = 0;
        for (Map.Entry<String, Integer> entry : dereceler.entrySet()) {
            if (count < 3) {
                System.out.println(entry.getKey() + " - " + entry.getValue());
                count++;
            } else {
                break;
            }
        }
    }

    public static int enDusukZamanaSahipKisi(Map<String, Integer> dereceler) {
        int enDusukZaman = Integer.MAX_VALUE;
        for (int zaman : dereceler.values()) {
            if (zaman < enDusukZaman) {
                enDusukZaman = zaman;
            }
        }
        return enDusukZaman;
    }

    public static int ikinciEnIyiKosucuyuBul(Map<String, Integer> dereceler, int enDusukZaman) {
        int ikinciEnIyiZaman = Integer.MAX_VALUE;
        for (int zaman : dereceler.values()) {
            if (zaman > enDusukZaman && zaman < ikinciEnIyiZaman) {
                ikinciEnIyiZaman = zaman;
            }
        }
        return ikinciEnIyiZaman;
    }

    public static void siniflandirmayiYap(Map<String, Integer> dereceler) {
        int A = 0, B = 0, C = 0;
        for (int zaman : dereceler.values()) {
            if (zaman >= 200 && zaman <= 299) {
                A++;
            } else if (zaman >= 300 && zaman <= 399) {
                B++;
            } else if (zaman >= 400) {
                C++;
            }
        }
        System.out.println("A -> " + A + ", B -> " + B + ", C -> " + C);
    }

    public static <T, E> T getKeyByValue(Map<T, E> map, E value) {
        for (Map.Entry<T, E> entry : map.entrySet()) {
            if (value.equals(entry.getValue())) {
                return entry.getKey();
            }
        }
        return null;
    }
}
