import java.io.BufferedWriter;
import java.io.FileWriter;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.ArrayList;
import java.util.List;
import java.util.Stack;

/**
 *
 * @author victor
 */
public class ValidaLinhas {

    public static void main(String[] args) throws Exception{
        
        String values = "([{<)]}>";
        List<String> list = new ArrayList<>();
        
        for(String line : Files.readAllLines(Paths.get(args[0]))) {
            
            Stack<Integer> arr = new Stack<>();
            boolean correct = true;
            for(int i = 0; i < line.length(); i++) {
                int index = values.indexOf(line.charAt(i));
                
                if(index >= 0 && index < 4){
                    arr.add(index);
                } else if(index >= 4 || index == -1){
                    if(arr.empty() || arr.pop() != index - 4){
                        list.add(line + " - Inválido");
                        correct = false;
                        break;
                    }
                }
            }
            
            if(correct)
                list.add(line + " - OK");
        }
        
        try (FileWriter fstream = new FileWriter("output" + args[0]);
             BufferedWriter info = new BufferedWriter(fstream)) {
            for (int i = 0; i < list.size(); i++) {
                info.write(String.format(list.get(i) + "\n"));
            }
        }
    }
}
