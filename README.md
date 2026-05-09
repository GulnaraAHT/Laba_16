import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class Main {
    public static void main(String[] args) {

        String fileCom = "C:\\Users\\user\\Documents\\file\\fileCom.txt";
        String fileNoCom = "C:\\Users\\user\\Documents\\file\\fileNoCom.txt";
        try {
            String code = Files.readString(Path.of(fileCom));
            code = code.replaceAll("/\\*[\\s\\S]*?\\*/", "");
            code = code.replaceAll("//.*", "");
            code = code.replaceAll("\\n\\s*\\n", "\n");
            Files.writeString(Path.of(fileNoCom), code);

            System.out.println("Файл записан без комментаиев!");
        }
        catch(IOException e) {
            System.out.println("Ошибка, что-то ни так");
        }

    }
}
