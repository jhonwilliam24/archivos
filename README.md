# 
import java.util.Scanner; 
import java.io.*; 
import java.util.Arrays;
import java.util.Collections;
import java.util.HashSet;
import java.util.LinkedList;
import java.util.List;
import java.util.Random;
public class archivos{     
        private static String Var_identifier;
        private static List<String> var_id1 = new LinkedList<>();
        private static List<String> var_id2 = new LinkedList<>();
        private static List<String> var_id3 = new LinkedList<>();
public static void modify(){
try{
    Scanner leer=new Scanner(System.in);  
    String texto=""; 
    char x; 
    FileReader input=new FileReader("C:\\Users\\jhon\\Desktop\\archivos\\"+Var_identifier); 
        int c=input.read(); 
        while (c!=-1){ 
            x=(char) (c); 
            texto=texto + x; 
            c=input.read();} 
         //System.out.println(texto); //muestra la cadena de texto 
            input.close();
            String text=""; 
            FileWriter output=new FileWriter("C:\\Users\\jhon\\Desktop\\archivos\\"+Var_identifier);
            System.out.println("digite Texto"); 
            text=leer.nextLine();
            texto=texto+text;
            output.write(texto+ ",");
            output.close();//cierre de las operaciones de escritura en el archivo 
            }
   catch (IOException ex){
   System.out.println("Un error ha ocurrido");}
   comandos();
   }
public static void duplicate(){
    try{
         System.out.println("digite el nombre de archivo") ;     
         FileWriter output=new FileWriter("C:\\Users\\jhon\\Desktop\\archivos\\"+" 2"+Var_identifier); //inicio de la escritura en el archivo
         for(Object o : var_id2){
        //Si no coincide el primer y último index => están repetidas
        if(var_id2.indexOf(o) != var_id2.lastIndexOf(o))
        output.write((String) o+",");}
        output.close();}
         catch (IOException ex){
         System.out.println("Un error ha ocurrido"); 
      }
        HashSet hs = new HashSet();
    //Lo cargamos con los valores del array, esto hace quite los repetidos
        hs.addAll(var_id2);
    //Limpiamos el array
        var_id2.clear();
    //Agregamos los valores sin repetir
        var_id2.addAll(hs);
    for(int i=0;i<var_id2.size();i++){
            System.out.println(var_id2.get(i));}
            comandos();
  } 
   //**************************************************//
  public static void order(){ 
      try {
      final BufferedReader reader = new BufferedReader(
      new FileReader("C:\\Users\\jhon\\Desktop\\archivos\\"+Var_identifier));
      String line = "";   
      var_id2.clear();
      while((line = reader.readLine())!= null) {
      var_id2.addAll(Arrays.asList(line.split(",")));}
      Collections.sort(var_id2); 
      for(int a=0;a<var_id2.size();a++){
      System.out.println(var_id2.get(a));}
      comandos();
       reader.close();
     }  catch (FileNotFoundException e) 
        {e.printStackTrace();} 
        catch (IOException e) 
        {e.printStackTrace();} 
     }
 public static void random() throws IOException{
 Random r = new Random();
    try{
        java.util.Scanner scanner = new Scanner(System.in);
        System.out.print("Introduzca cantidad de caracteres: ");
        int n = scanner.nextInt();
        File file = new File("C:\\Users\\jhon\\Desktop\\archivos\\"+Var_identifier);
        FileWriter fw = new FileWriter(file.getAbsoluteFile());
        BufferedWriter bw = new BufferedWriter(fw);
    for(int i=0; i<n; i++) {
        int valorLetra =(char)(Math.random()*26+65);
        char guardar=(char) valorLetra;
        String cadena = Character.toString(guardar);
        //output.write(cadena+",");
        fw.write(cadena+",");}
        bw.close();
        //output.close();
         comandos();}
         catch (IOException ex){
         System.out.println("Un error ha ocurrido"); 
        }
  }
  //******************************************************//
public static void read(){
    try {
        final BufferedReader reader = new BufferedReader(
        new FileReader("C:\\Users\\jhon\\Desktop\\archivos\\"+Var_identifier));
        String line = ""; 
        var_id2.clear();
            while((line = reader.readLine())!= null) {
                var_id2.addAll(Arrays.asList(line.split(" ,"))) ;} 
                System.out.println(var_id2);
                reader.close();
                comandos();
         }  catch (FileNotFoundException e){e.printStackTrace();} 
            catch (IOException e){e.printStackTrace();}}
 //***************************************************//  
 public static void assign(){
    try{
         System.out.println(" se va crear  un archivo ");
         java.util.Scanner scanner = new Scanner(System.in);
             System.out.println("digite el nombre de archivo") ;     
             Var_identifier = scanner.next()+".txt"; 
         FileWriter output=new FileWriter("C:\\Users\\jhon\\Desktop\\archivos\\"+Var_identifier); //inicio de la escritura en el archivo
         output.close();  
        }
         catch (IOException ex){
         System.out.println("Un error ha ocurrido"); 
      }
    comandos();
   }
//************************************************************//
 public static void comandos(){
  java.util.Scanner scanner = new Scanner(System.in);
  System.out.println("digite el comando > ");
  String request = scanner.next();
  try {
      final BufferedReader reader = new BufferedReader(
      new FileReader("C:\\Users\\jhon\\Desktop\\archivos\\comandos.txt"));
      String line = "";   
      while((line = reader.readLine())!= null) {
      String[] token = line.split(",",-1);
    
            int len = Math.min(token.length, 25); 
            for (int i = 0; i<len;i++){
                while (token[i].equalsIgnoreCase(request)) {
                 if (token[i].equalsIgnoreCase("assign")){assign();}
                 if (token[i].equalsIgnoreCase("read")){read();}
                 if (token[i].equalsIgnoreCase("modify")){modify();}
                 if (token[i].equalsIgnoreCase("order")){order();}
                 if (token[i].equalsIgnoreCase("duplicate")){duplicate();} 
                 if (token[i].equalsIgnoreCase("random")){random();}
                } 
              }
           } 
        reader.close();
        comandos();
         }
        catch (FileNotFoundException e) 
        {e.printStackTrace();} 
        catch (IOException e) 
        {e.printStackTrace();}
        }
 public static void main(String[] args) {
        System.out.println(
                  "*********************************************\n" +
                  "*    Universidad Autonoma de Colombia       *\n" +
                  "*       Naranjo Muñoz Jhon William          *\n" +
                  "*               Algoritmia                  *\n" +
                  "*            Alexander cardona              *\n" +
                  "*            Manejo de Archivos             *\n"+
                  "*********************************************\n"+
                  "*********************************************\n"+
                  "*********************************************\n"+
                  "* Comandos:                                 *\n"+ 
                  "* assign,read,random,modify,order,duplicate *\n"+
                  "*********************************************");
      comandos();
   }
 }   
   
