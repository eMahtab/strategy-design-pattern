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


```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class App {

	public static void main(String[] args) {
	    List<Player> players = new ArrayList<>();
	    Player player1 = new Player(59, "John", 26);
	    Player player2 = new Player(67, "Voger", 24);
	    Player player3 = new Player(45, "Steven", 23);
	    players.add(player1);
	    players.add(player2);
	    players.add(player3);
	    
	    PlayerOrderByRanking rankComparator = new PlayerOrderByRanking();
	    Collections.sort(players, rankComparator);
	    System.out.println("Order by Ranking : " + players);
	    
	    PlayerOrderByAge ageComparator = new PlayerOrderByAge();
	    Collections.sort(players, ageComparator);
	    System.out.println("Order by Age : " + players);
	    
	    PlayerOrderByName nameComparator = new PlayerOrderByName();
	    Collections.sort(players, nameComparator);
	    System.out.println("Order by Name : " + players);
	    
	}

}

```

### Result
```
Order by Ranking : [Steven, John, Voger]
Order by Age : [Steven, Voger, John]
Order by Name : [John, Steven, Voger]

```

# References :
https://www.baeldung.com/java-comparator-comparable

