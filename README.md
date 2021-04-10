# winnerpackage main;

public class Jungle {
	public static void main(String[] s) {
		Competition competition = new Competition();
		competition.compete();
	}
}

class RandomStrengthGenerator {
	public static int getRandomNumber(int min, int max) {
	    return (int) ((Math.random() * (max - min)) + min);
	}
}


class Competition {
	private Feline[] lions;
	private Feline[] tigers;
	
	
	public void compete(){
		
		create();
		
		fight();
	}
	
	
	public void create(){
		lions = new Lion[10];
		tigers = new Tiger[10];
		for(int i= 0; i<10; i++){
			lions[i] = new Lion();
			tigers[i] = new Tiger();
		}
	}
	
	public void fight(){
		int numberOfAnimals = lions.length;
		for(int i = 0 ; i < numberOfAnimals ; i++) {
			int tigerStrength = tigers[i].getStrength();
			int lionStrength = lions[i].getStrength();
			int round = i+1;
			
			
			System.out.println("Fight Round "+round+": Tiger Strength - "+tigerStrength+", Lion Strength - "+lionStrength);
			
			
			if(tigerStrength > lionStrength) System.out.println("Tiger Wins");
			else  System.out.println("Lion Wins");
			
			
			System.out.println();
		}
	}

}

class Feline {
	private String name;
	private int strength;
	
	

	public Feline(int strength){
		this.strength = strength;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getStrength() {
		return strength;
	}

	public void setStrength(int strength) {
		this.strength = strength;
	}
}

class Lion extends Feline {
	public Lion() {
		super(RandomStrengthGenerator.getRandomNumber(77,120));
	}
}

class Tiger extends Feline {
	public Tiger() {
		super(RandomStrengthGenerator.getRandomNumber(160, 180));
	}
}
