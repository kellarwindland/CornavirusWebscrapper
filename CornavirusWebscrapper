import java.io.IOException;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import components.simplewriter.SimpleWriter;
import components.simplewriter.SimpleWriter1L;

public final class Corona {

    private Corona() {
    }

    /**
     * Main method.
     *
     * @param args
     *            the command line arguments; unused here
     * @throws IOException
     */
    public static void main(String[] args) throws IOException {
        SimpleWriter out = new SimpleWriter1L();
        Document d = Jsoup
                .connect(
                        "https://www.worldometers.info/coronavirus/country/us/")
                .timeout(6000).get();
        Element ele = d.select("table#usa_table_countries_today").get(0);
        Elements body = ele.select("tbody");
        int i = 0;
        Object[][] Data = new Object[63][10];
        for (Element trelement : body.select("tr")) {
            if (i < 63) {
                Elements tdelement = trelement.select("td");
                int count = 0;
                int j = 0;
                for (Element element : tdelement) {
                    String str = element.select("td").text();
                    if (count < 10) {
                        if (!str.equals("")) {
                            if (isInteger(str)) {
                                System.out.print(Integer.parseInt(str));
                                System.out.print("\t");
                                Data[i][j] = str;
                            } else {
                                System.out.print(str);
                                System.out.print("\t");
                                Data[i][j] = str;
                            }
                        } else {
                            System.out.print(0);
                            System.out.print("\t");
                        }
                    }
                    j++;
                    count++;
                }
                System.out.println();
            }
            i++;
        }

        String path = "C:\\Users\\Kellar Windland\\Desktop\\Java Projects\\Corona.xlsx";

        //do the logic for excel sheet

        out.close();
    }

    public static boolean isInteger(String str) {
        boolean result = true;
        int length = 0;
        if (str == null) {
            return false;
        } else {
            length = str.length();
        }

        if (str.charAt(0) == '+' || str.charAt(0) == '-') {
            result = false;
        }

        for (int i = 0; i < length; i++) {
            char c = str.charAt(i);
            if (c < '0' || c > '9') {
                result = false;
            }
        }

        return result;

    }

}
