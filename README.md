# Dart-Game
A dart game user enters the dart number then generates random coordinates and determine the regions
public class dartGame {
     public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("**********************************************");
        System.out.println("DART GAME !");
        System.out.print("Enter the number of darts to be thrown: ");
        int darts = scanner.nextInt();
        System.out.println("**********************************************");
        int dart = 1;
        
        int countA = 0;
        int countB = 0;
        int countC = 0;
        int countD = 0;
        int countE = 0;
        int countF = 0;
        int countG = 0;
        int countUD = 0 ;
        
        while(dart <= darts){
            
            double xcordinate = (int)((Math.random()*100) - 50) / 10.0;
            double ycordinate = (int)((Math.random()*100) - 50) / 10.0;
            
            System.out.println("Dart " + dart);
            System.out.println("Cordinates: ( "+xcordinate+","+ycordinate+" )" );
            
            if(xcordinate == 0 || ycordinate == 0){
                //This condiditon checks if the point is on x-axis or y-axis or not.
                System.out.println("Region: Undecided");
                countUD++; 
                dart++;
                System.out.println("----------------------------------------");
            }
            
            
            
            else if(xcordinate>0.0 && ycordinate>0.0){
                //This condition checks if the point is in the FIRST zone of the cordinate system or not.
                if(xcordinate + ycordinate < 5.0){
                    //This condition checks if the point is in the Region A or not.
                    System.out.println("Region: A");
                    countA++;
                    dart++;
                    System.out.println("----------------------------------------");
                    continue;
                }
                else if(xcordinate + ycordinate == 5.0 || xcordinate == 5.0 || ycordinate == 5.0){
                    //This condition checks if the point is on the line seperating the Region A and B or on the line that defines our cordinate system boundaries of the first zone.
                    System.out.println("Region: Undecided");
                    countUD++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
                else{
                    //When sum of xcordinate and ycordinate is bigger then than 5 and if the point is not on the boundary lines, this block will be executed. That means the point is in the Region B.
                    System.out.println("Region: B");
                    countB++;
                    dart++;
                    System.out.println("----------------------------------------");
                }   
            }
            
            
            else if(xcordinate<0.0 && ycordinate>0.0){
                //This condition checks if the point is in the SECOND zone of the cordinate system or not.
                if(xcordinate == -5.0 || ycordinate == 5.0){
                    //This condition checks if the point is on the boundary lines of the cordinate system of the second zone or not.
                    System.out.println("Region: Undecided");
                    countUD++;
                    dart++;
                    System.out.println("----------------------------------------");
                    continue;  
                }
                else if(Math.pow(Math.abs(ycordinate-2.5),2) + Math.pow(Math.abs(xcordinate-(-2.5)),2) < Math.pow(1.25,2)){
                    //This condition checks if the point is in the circle or not, by distance between two points formula.
                    System.out.println("Region: C");
                    countC++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
                else if(Math.pow(Math.abs(ycordinate-2.5),2) + Math.pow(Math.abs(xcordinate-(-2.5)),2) == Math.pow(1.25,2)){
                    //This condition checks if the point is on the line of the circle or not.
                    System.out.println("Region: Undecided");
                    countUD++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
                else{
                    //When the point is in the Region G, this block will be executed.
                    System.out.println("Region: G");
                    countG++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
            }
            
            
            
            else if(xcordinate<0.0 && ycordinate<0.0){
                //This condition checks if the point is in the THIRD zone of the cordinate sytsme or not.
                if(xcordinate == -5.0 || ycordinate == -5.0 || xcordinate == ycordinate){
                    //This condition checks if the point is on the boundaries of the cordinate system of the third zone or the line seperating the Region D and E or not.
                    System.out.println("Region: Undecided");
                    countUD++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
                else if(Math.abs(ycordinate) < Math.abs(xcordinate)){
                    //This condition checks if the point is in the Region D or not.
                    System.out.println("Region: D");
                    countD++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
                else{
                    //When the point is in the Region E, this block will be executed.
                    System.out.println("Region: E");
                    countE++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
            }
            
            else{
                //When the point is in the FOURTH zone of the cordinate system, this block will be executed.
                if(xcordinate == 5.0 && ycordinate == -5.0){
                    //This condition checks if the point is on the boundary lines of the cordinate system of fourth zone.
                    System.out.println("Region: Undecided");
                    countUD++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
                else{
                    //In the fourth zone; if the point is not on the boundary lines, this block will be executed.
                    System.out.println("Region: F");
                    countF++;
                    dart++;
                    System.out.println("----------------------------------------");
                }
            }
 
        }
        
        
        
        System.out.println("Region Statistics:");
        System.out.println("Region A: "+ countA + " dart " + "(" +(int)(((double)countA/darts)*1000)/10.0+ "%)");
        System.out.println("Region B: "+ countB + " dart " + "(" +(int)(((double)countB/darts)*1000)/10.0+ "%)");
        System.out.println("Region C: "+ countC + " dart " + "(" +(int)(((double)countC/darts)*1000)/10.0+ "%)");
        System.out.println("Region D: "+ countD + " dart " + "(" +(int)(((double)countD/darts)*1000)/10.0+ "%)");
        System.out.println("Region E: "+ countE + " dart " + "(" +(int)(((double)countE/darts)*1000)/10.0+ "%)");
        System.out.println("Region F: "+ countF + " dart " + "(" +(int)(((double)countF/darts)*1000)/10.0+ "%)");
        System.out.println("Region G: "+ countG + " dart " + "(" +(int)(((double)countG/darts)*1000)/10.0+ "%)");
        System.out.println("Undecided: "+ countUD + " dart " + "(" +(int)(((double)countUD/darts)*1000)/10.0+ "%)");
        
        
    }
}
