# Strategy Design Pattern

The Strategy pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from the clients that use it.

![Strategy Pattern](strategy-pattern.PNG?raw=true)


```java
public class Player {
	private int ranking;
    private String name;
    private int age;
    
	public Player(int ranking, String name, int age) {
		this.ranking = ranking;
		this.name = name;
		this.age = age;
	}
	public int getRanking() {
		return ranking;
	}
	
	public String getName() {
		return name;
	}
	
	public int getAge() {
		return age;
	}
	
	public String toString() {
		return name;
	}
	
}



import java.util.Comparator;

public class PlayerOrderByRanking implements Comparator<Player>{

	@Override
	public int compare(Player p1, Player p2) {
		return Integer.compare(p1.getRanking(), p2.getRanking());
	}
	
}


import java.util.Comparator;

public class PlayerOrderByAge implements Comparator<Player>{

	@Override
	public int compare(Player p1, Player p2) {
		return Integer.compare(p1.getAge(), p2.getAge());
	}
	
}

import java.util.Comparator;

public class PlayerOrderByName implements Comparator<Player>{

	@Override
	public int compare(Player p1, Player p2) {
		return p1.getName().compareTo(p2.getName());
	}
	
}


```


