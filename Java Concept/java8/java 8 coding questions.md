# String

## CharArrayToString

```java
package String;

import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CharArrayToString {
    public static void main(String args[]){
        char arr[ ] = {'H', 'e', 'l', 'l', 'o'};
        char ch_arr[] = {'H','e','l','l','o',' ','W','o','r','l','d','!'};
        //Using String class Constructor
        String str1 = new String(ch_arr);
        System.out.println("String: "+ str1);

        //Using StringBuilder Class
        StringBuilder sb_obj = new StringBuilder();
        for(int i = 0; i < ch_arr.length; i++){
            sb_obj.append(ch_arr[i]);
        }
        System.out.println("StringBuilder: " + sb_obj);

        //Using valueOf() method of String class
        String s1 = String.valueOf(ch_arr);
        System.out.println("String: "+s1);

        //Using copyValueOf() method of String class
        String s2 = String.copyValueOf(ch_arr);
        System.out.println("String: " + s2);
        // Extracting substring from ch_arr
        String substring = String.copyValueOf(ch_arr, 4, 4);
        // Printing output in form of string
        System.out.println("Substring: "+substring);

        //Using Collectors in Streams
        String string_op = Stream
                .of(ch_arr)
                .map(charr -> new String(charr))
                .collect(Collectors.joining());

        // Printing the string received from Collectors
        System.out.println("String Output: " + string_op);
    }
}
```

## DuplicateString

```java
package DuplicateString;

import java.util.*;
import java.util.function.Function;
import java.util.stream.Collectors;

public class DuplicateString {
    public static void main(String args[]){
        String sentence="alex brain charles alex charles david eric david";

        List<String> wordsList= Arrays.stream(sentence.split(" ")).collect(Collectors.toList());

        findDuplicateWords(wordsList);

        findDuplicateWords_Second(wordsList);

        findDuplicateWords_Third(wordsList);

        findDuplicateWords_Fourth(wordsList);

        findDuplicateWords_Fifth(wordsList);

        findDuplicateWords_Sixth(wordsList);

        findDuplicateWords_Seventh(wordsList);

        findDuplicateWords_Eight(wordsList);
    }
```
```java
    public static void findDuplicateWords(List<String> wordsList){
        System.out.println("----------------------In method findDuplicateWords------------------");
        Set<String> tempSet=new HashSet<>();

        List<String> dublicateWords=wordsList.stream().filter(s->!tempSet.add(s)).collect(Collectors.toList());

        System.out.println(dublicateWords);
    }
```
```java
    public static void findDuplicateWords_Second(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Second------------------");
        Set<String> tempSet=new HashSet<>();

        Map<String,Integer> wordsMapWithCount=wordsList.stream()
                .collect(Collectors.toMap(Function.identity(),word->1,Math::addExact));

        System.out.println(wordsMapWithCount);

        Map<String, Integer> dupWordsMapWithCount=wordsMapWithCount
                .entrySet()
                .stream()
                .filter(e->e.getValue()>1)
                .collect(Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue));

        System.out.println(dupWordsMapWithCount);
    }
```
```java
    public static void findDuplicateWords_Third(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Third------------------");

        Map<String,Integer> dupWordsMapWithCount=wordsList.stream()
                .collect(Collectors.toMap(Function.identity(),word->1,Math::addExact))
                .entrySet()
                .stream()
                .filter(e->e.getValue()>1)
                .collect(Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue));


        System.out.println(dupWordsMapWithCount);
    }
```
```java
    public static void findDuplicateWords_Fourth(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Fourth------------------");

        wordsList.stream()
                .collect(Collectors.toMap(Function.identity(),word->1,Math::addExact))
                .entrySet()
                .stream()
                .filter(e->e.getValue()>1)
                .collect(Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue))
                .entrySet()
                .forEach(e->{System.out.println(e.getKey());});


        System.out.println("In key value pair");

        wordsList.stream()
                .collect(Collectors.toMap(Function.identity(),word->1,Math::addExact))
                .entrySet()
                .stream()
                .filter(e->e.getValue()>1)
                .collect(Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue))
                .forEach((K,V)->{System.out.println(K);});
    }
```
```java
    public static void findDuplicateWords_Fifth(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Fifth------------------");

        System.out.println(" Using simple Java");
        Set<String> tempSet=new HashSet<>();
        List<String> duplicateWords=new ArrayList<>();
        for(String word:wordsList){
            if(!tempSet.add(word)){
                duplicateWords.add(word);
                System.out.println(word);
            }
        }
        System.out.println(duplicateWords);
    }
```
```java
    public static void findDuplicateWords_Sixth(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Sixth------------------");

        System.out.println(" Using simple Java");
        Map<String, Integer> dupWordsMapWithCount=new HashMap<>();
        for(String word:wordsList){
            dupWordsMapWithCount.put(word,Collections.frequency(wordsList,word));
        }
        System.out.println(dupWordsMapWithCount);
        dupWordsMapWithCount.forEach((K,V)->{if(V>1)System.out.println(K);});
    }
```
```java
    public static void findDuplicateWords_Seventh(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Seventh------------------");

        System.out.println("========= Using simple Java===========");
        Set<String> tempSet=new HashSet<>();
        Map<String, Integer> dupWordsMapWithCount=new HashMap<>();
        for(String word:wordsList){
            if(Collections.frequency(wordsList,word)>1) {
                dupWordsMapWithCount.put(word, Collections.frequency(wordsList, word));
                tempSet.add(word);
            }
        }
        System.out.println(dupWordsMapWithCount);
        System.out.println(tempSet);
    }
```
```java
    public static void findDuplicateWords_Eight(List<String> wordsList){

        System.out.println("----------------------In method findDuplicateWords_Eight------------------");

        System.out.println("==Print Each Word Frequency==");
        wordsList.stream()
                .collect(Collectors.toSet())
                .forEach(word->{System.out.println(word+" : "+Collections.frequency(wordsList,word));});

        System.out.println("==Duplicate Word==");
        wordsList.stream()
                .collect(Collectors.toSet())
                .stream()
                .filter(word->Collections.frequency(wordsList,word)>1)
                .forEach(word->{System.out.println(word);});

    }
}
```

## DuplicateNumber

```java
package DuplicateNumber;

import java.util.*;
import java.util.function.Function;
import java.util.stream.Collectors;

public class DuplicateNumber {
    public static void main(String args[]){

        List<Integer> list = Arrays.asList(1, 2, 3, 3, 4, 4, 5);
        //Using the contains() Method of Set
        List<Integer> duplicates = listDuplicateUsingSet(list);
        System.out.println(duplicates);

        //Using a Map and Storing the Frequency of Elements
        duplicates =listDuplicateUsingMap(list);
        System.out.println(duplicates);

        //Using filter() and Set.add() Method using 8
        duplicates =listDuplicateUsingFilterAndSetAdd(list);
        System.out.println(duplicates);

        //Using Collections.frequency() using 8
        duplicates =listDuplicateUsingCollectionsFrequency(list);
        System.out.println(duplicates);

        //Using Map and Collectors.groupingBy() using 8
        duplicates =listDuplicateUsingMapAndCollectorsGroupingBy(list);
        System.out.println(duplicates);



    }
```
```java
    private static List<Integer> listDuplicateUsingFilterAndSetAdd(List<Integer> list) {
        Set<Integer> elements = new HashSet<Integer>();
        return list.stream()
                .filter(n -> !elements.add(n))
                .collect(Collectors.toList());
    }
```
```java
    private static List<Integer> listDuplicateUsingCollectionsFrequency(List<Integer> list) {
        List<Integer> duplicates = new ArrayList<>();
        Set<Integer> set = list.stream()
                .filter(i -> Collections.frequency(list, i) > 1)
                .collect(Collectors.toSet());
        duplicates.addAll(set);
        return duplicates;
    }
```
```java
    private static List<Integer> listDuplicateUsingMapAndCollectorsGroupingBy(List<Integer> list) {
        List<Integer> duplicates = new ArrayList<>();
        Set<Integer> set = list.stream()
                .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()))
                .entrySet()
                .stream()
                .filter(m -> m.getValue() > 1)
                .map(Map.Entry::getKey)
                .collect(Collectors.toSet());
        duplicates.addAll(set);
        return duplicates;
    }
```
```java
    private static List<Integer> listDuplicateUsingSet(List<Integer> list) {
        List<Integer> duplicates = new ArrayList<>();
        Set<Integer> set = new HashSet<>();
        for (Integer i : list) {
            if (set.contains(i)) {
                duplicates.add(i);
            } else {
                set.add(i);
            }
        }
        return duplicates;
    }
```
```java
    private static List<Integer> listDuplicateUsingMap(List<Integer> list) {
        List<Integer> duplicates = new ArrayList<>();
        Map<Integer, Integer> frequencyMap = new HashMap<>();
        for (Integer number : list) {
            frequencyMap.put(number, frequencyMap.getOrDefault(number, 0) + 1);
        }
        for (int number : frequencyMap.keySet()) {
            if (frequencyMap.get(number) != 1) {
                duplicates.add(number);
            }
        }
        return duplicates;
    }
}
```

## Employee Real Time Queries

```java
package Employee;

class Employee
{
    int id;
     
    String name;
     
    int age;
     
    String gender;
     
    String department;
     
    int yearOfJoining;
     
    double salary;
     
    public Employee(int id, String name, int age, String gender, String department, int yearOfJoining, double salary) 
    {
        this.id = id;
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.department = department;
        this.yearOfJoining = yearOfJoining;
        this.salary = salary;
    }
     
    public int getId() 
    {
        return id;
    }
     
    public String getName() 
    {
        return name;
    }
     
    public int getAge() 
    {
        return age;
    }
     
    public String getGender() 
    {
        return gender;
    }
     
    public String getDepartment() 
    {
        return department;
    }
     
    public int getYearOfJoining() 
    {
        return yearOfJoining;
    }
     
    public double getSalary() 
    {
        return salary;
    }
     
    @Override
    public String toString() 
    {
        return "Id : "+id
                +", Name : "+name
                +", age : "+age
                +", Gender : "+gender
                +", Department : "+department
                +", Year Of Joining : "+yearOfJoining
                +", Salary : "+salary;
    }
}
```

```java
package Employee;

import java.util.*;
import java.util.stream.Collectors;

public class EmployeeUsingMap {
    public static void main(String args[]){
        Map<String,Integer> map = new HashMap<>();
        map.put("anil",1000);
        map.put("ankit",1200);
        map.put("bhavna",1300);
        map.put("james",1400);
        map.put("micael",1500);
        map.put("tom",1600);
        map.put("daniel",1700);

        Map<String,Integer> map2 = new HashMap<>();
        map2.put("anil",1000);
        map2.put("ankit",1200);
        map2.put("bhavna",1200);
        map2.put("james",1200);
        map2.put("micael",1000);
        map2.put("tom",1300);
        map2.put("daniel",1300);

        //fetch second highest salary with employee name.
        secondMaxSalaryEmployee(map);

        secondMaxSalaryEmployee1(map2);

        secondMaxSalaryEmployee2(map2);

        secondMaxSalaryEmployee3(map2);
    }
    public static void secondMaxSalaryEmployee(Map<String,Integer> mapEmp) {
        Map.Entry<String,Integer> finalResult = mapEmp.entrySet()
                .stream()
                .sorted(Comparator.comparing(entry -> -entry.getValue())) // minus make it to do in desc order
                .toList()
                .get(1); // index start from 0
        System.out.println(finalResult);
    }

    public static void secondMaxSalaryEmployee1(Map<String,Integer> mapEmp) {
        Map<Integer,List<String>> interimResult =
                mapEmp.entrySet()
                        .stream()
                        .collect(Collectors.groupingBy(entry ->entry.getValue(),
                                Collectors.mapping(entry -> entry.getKey(),Collectors.toList())
                        ));
        System.out.println(interimResult);
    }

    public static void secondMaxSalaryEmployee2(Map<String,Integer> mapEmp) {
        List<Map.Entry<Integer, List<String>>> finalResult2 = mapEmp.entrySet()
                .stream()
                .collect(Collectors.groupingBy(entry -> entry.getValue(),
                        Collectors.mapping(entry -> entry.getKey(), Collectors.toList())
                ))
                .entrySet()
                .stream()
                .sorted(Comparator.comparing(it -> -it.getKey())) // minus sign for decreasing order
                .toList();
        System.out.println(finalResult2);
    }

    public static void secondMaxSalaryEmployee3(Map<String,Integer> mapEmp) {
        Map.Entry<Integer,List<String>> finalResult2 = mapEmp.entrySet()
                .stream()
                .collect(Collectors.groupingBy(entry ->entry.getValue(),
                        Collectors.mapping(entry -> entry.getKey(),Collectors.toList())
                ))
                .entrySet()
                .stream()
                .sorted(Comparator.comparing(it -> it.getKey()))
                .toList()
                .get(1);

        System.out.println(finalResult2);
    }


}
```

```java
package Employee;

import java.util.*;
import java.util.Map.*;
import java.util.stream.Collectors;

public class RealTimeQueries {
    public static void main(String args[]){
        List<Employee> employeeList = new ArrayList<>();

        employeeList.add(new Employee(111, "Jiya Brein", 32, "Female", "HR", 2011, 25000.0));
        employeeList.add(new Employee(122, "Paul Niksui", 25, "Male", "Sales And Marketing", 2015, 13500.0));
        employeeList.add(new Employee(133, "Martin Theron", 29, "Male", "Infrastructure", 2012, 18000.0));
        employeeList.add(new Employee(144, "Murali Gowda", 28, "Male", "Product Development", 2014, 32500.0));
        employeeList.add(new Employee(155, "Nima Roy", 27, "Female", "HR", 2013, 22700.0));
        employeeList.add(new Employee(166, "Iqbal Hussain", 43, "Male", "Security And Transport", 2016, 10500.0));
        employeeList.add(new Employee(177, "Manu Sharma", 35, "Male", "Account And Finance", 2010, 27000.0));
        employeeList.add(new Employee(188, "Wang Liu", 31, "Male", "Product Development", 2015, 34500.0));
        employeeList.add(new Employee(199, "Amelia Zoe", 24, "Female", "Sales And Marketing", 2016, 11500.0));
        employeeList.add(new Employee(200, "Jaden Dough", 38, "Male", "Security And Transport", 2015, 11000.5));
        employeeList.add(new Employee(211, "Jasna Kaur", 27, "Female", "Infrastructure", 2014, 15700.0));
        employeeList.add(new Employee(222, "Nitin Joshi", 25, "Male", "Product Development", 2016, 28200.0));
        employeeList.add(new Employee(233, "Jyothi Reddy", 27, "Female", "Account And Finance", 2013, 21300.0));
        employeeList.add(new Employee(244, "Nicolus Den", 24, "Male", "Sales And Marketing", 2017, 10700.5));
        employeeList.add(new Employee(255, "Ali Baig", 23, "Male", "Infrastructure", 2018, 12700.0));
        employeeList.add(new Employee(266, "Sanvi Pandey", 26, "Female", "Product Development", 2015, 28900.0));
        employeeList.add(new Employee(277, "Anuj Chettiar", 31, "Male", "Product Development", 2012, 35700.0));


        //How many male and female employees are there in the organization?
        maileAndFemaleCount(employeeList);

        //Print the name of all departments in the organization?
        displayNameOfDepartments(employeeList);

        //What is the average age of male and female employees?
        averageAgeOfMaleAndFemale(employeeList);

        //Get the details of highest paid employee in the organization?
        highestPaidEmployeeWrapper(employeeList);
        highestPaidEmployeeWrapper2(employeeList);

        //Get the names of all employees who have joined after 2015?
        empNamesJoinAfter2015(employeeList);
        empNamesJoinAfter2015_2(employeeList);

        //Count the number of employees in each department?
        numberOfEmployeeInEachDepartment(employeeList);

        //What is the average salary of each department?
        averageSalaryOfEachDepartment(employeeList);

        //Get the details of youngest male employee in the product development department?
        youngestMaleEmployeeInProductDevelopment(employeeList);
        youngestMaleEmployee(employeeList);

        //Who has the most working experience in the organization?
        mostWorkingExperiencedEmployee(employeeList);

        //How many male and female employees are there in the sales and marketing team?
        countMaleFemaleEmployeesInSalesMarketing(employeeList);

        //What is the average salary of male and female employees?
        avgSalaryOfMaleAndFemaleEmployees(employeeList);

        //List down the names of all employees in each department?
        employeeListByDepartment(employeeList);

        // What is the average salary and total salary of the whole organization?
        employeeSalaryStatistics(employeeList);

        //Separate the employees who are younger or equal to 25 years from those employees who are older than 25 years.
        partitionEmployeesByAge(employeeList);

        //Who is the oldest employee in the organization? What is his age and which department he belongs to?
        oldestEmployeeWrapper(employeeList);

        //max salary employee by department
        maxSalaryEmployeeByDepartment(employeeList);

        //nth max salaried employee with with skip (n-1).
        secondMaxSalaryEmployee(employeeList);
        secondMaxSalaryEmployeeUsingToList(employeeList);
    }

    public static void maxSalaryEmployeeByDepartment(List<Employee> employeeList) {
        Map<String, Optional<Employee>> maxSalaryEmployeeByDepartment = employeeList.stream()
                .collect(Collectors.groupingBy(Employee::getDepartment,Collectors.maxBy(Comparator.comparingDouble(Employee::getSalary))));
        // Display the results
        maxSalaryEmployeeByDepartment.forEach((department, employee) -> {
            if (employee.isPresent()) {
                Employee emp = employee.get();
                System.out.println("Department: " + department +
                        ", Employee: " + emp.getName() +
                        ", Max Salary: " + emp.getSalary());
            }
        });
    }

    public static void secondMaxSalaryEmployee(List<Employee> employeeList) {
        Optional<Employee> emp = employeeList.stream()
                .sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).skip(1).findFirst();

        List<Employee>empl=employeeList.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).toList();

        System.out.println(emp.get());
    }

    public static void secondMaxSalaryEmployeeUsingToList(List<Employee> employeeList) {

        List<Employee>empList=employeeList.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).toList();

        System.out.println(empList.get(1).getSalary());
    }

    public static void maileAndFemaleCount(List<Employee> employeeList) {
        Map<String, Long> maileAndFemaleCount = employeeList.stream().collect(Collectors.groupingBy(Employee::getGender, Collectors.counting()));
        System.out.println(maileAndFemaleCount);
    }

    public static void displayNameOfDepartments(List<Employee> employeeList) {
        employeeList.stream().map(Employee::getDepartment).distinct().forEach(d->{
            System.out.println(d);
        });

    }

    public static void averageAgeOfMaleAndFemale(List<Employee> employeeList) {
        Map<String,Double> avgAgeOfMaleAndFemaleEmployees=employeeList.stream().collect(Collectors.groupingBy(Employee::getGender,Collectors.averagingInt(Employee::getAge)));
        System.out.println(avgAgeOfMaleAndFemaleEmployees);
    }


    public static void highestPaidEmployeeWrapper(List<Employee> employeeList) {
        Optional<Employee> highestPaidEmployeeWrapper=employeeList.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).findFirst();
        Employee highestPaidEmployee = highestPaidEmployeeWrapper.get();

        System.out.println("Details Of Highest Paid Employee : ");

        System.out.println("==================================");

        System.out.println("ID : "+highestPaidEmployee.getId());

        System.out.println("Name : "+highestPaidEmployee.getName());

        System.out.println("Age : "+highestPaidEmployee.getAge());

        System.out.println("Gender : "+highestPaidEmployee.getGender());

        System.out.println("Department : "+highestPaidEmployee.getDepartment());

        System.out.println("Year Of Joining : "+highestPaidEmployee.getYearOfJoining());

        System.out.println("Salary : "+highestPaidEmployee.getSalary());
    }

    public static void highestPaidEmployeeWrapper2(List<Employee> employeeList) {
        Optional<Employee> highestPaidEmployeeWrapper=employeeList.stream().collect(Collectors.maxBy(Comparator.comparingDouble(e->e.getSalary())));
        //highestPaidEmployeeWrapper=employeeList.stream().collect(Collectors.maxBy(Comparator.comparingDouble(Employee::getSalary)));
        Employee highestPaidEmployee = highestPaidEmployeeWrapper.get();

        System.out.println("Details Of Highest Paid Employee : ");

        System.out.println("==================================");

        System.out.println("ID : "+highestPaidEmployee.getId());

        System.out.println("Name : "+highestPaidEmployee.getName());

        System.out.println("Age : "+highestPaidEmployee.getAge());

        System.out.println("Gender : "+highestPaidEmployee.getGender());

        System.out.println("Department : "+highestPaidEmployee.getDepartment());

        System.out.println("Year Of Joining : "+highestPaidEmployee.getYearOfJoining());

        System.out.println("Salary : "+highestPaidEmployee.getSalary());
    }

    public static void empNamesJoinAfter2015(List<Employee> employeeList) {
        employeeList.stream().filter(e->e.getYearOfJoining()>2015).forEach(e->{
            System.out.println(e.getName());
        });
    }

    public static void empNamesJoinAfter2015_2(List<Employee> employeeList) {
        employeeList.stream()
                .filter(e -> e.getYearOfJoining() > 2015)
                .map(Employee::getName)
                .forEach(System.out::println);
    }

    public static void numberOfEmployeeInEachDepartment(List<Employee> employeeList){
        Map<String, Long>employeeCountByDepartment=employeeList.stream().collect(Collectors.groupingBy(Employee::getDepartment,Collectors.counting()));
        Set<Entry<String, Long>> entrySet = employeeCountByDepartment.entrySet();

        for (Entry<String, Long> entry : entrySet)
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }

    public static void averageSalaryOfEachDepartment(List<Employee> employeeList){
        Map<String, Double>avgSalaryOfDepartments=employeeList.stream().collect(Collectors.groupingBy(Employee::getDepartment,Collectors.averagingDouble(Employee::getSalary)));
        Set<Entry<String, Double>> entrySet = avgSalaryOfDepartments.entrySet();

        for (Entry<String, Double> entry : entrySet)
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }

    public static void youngestMaleEmployee(List<Employee> employeeList) {
        Optional<Employee> youngestEmployee=employeeList.stream().collect(Collectors.minBy(Comparator.comparingInt(Employee::getAge)));

        Employee youngestMaleEmployeeInProductDevelopment = youngestEmployee.get();

        System.out.println("Details Of Youngest Male Employee In Product Development");

        System.out.println("----------------------------------------------");

        System.out.println("ID : "+youngestMaleEmployeeInProductDevelopment.getId());

        System.out.println("Name : "+youngestMaleEmployeeInProductDevelopment.getName());

        System.out.println("Age : "+youngestMaleEmployeeInProductDevelopment.getAge());

        System.out.println("Year Of Joinging : "+youngestMaleEmployeeInProductDevelopment.getYearOfJoining());

        System.out.println("Salary : "+youngestMaleEmployeeInProductDevelopment.getSalary());
    }

    public static void youngestMaleEmployeeInProductDevelopment(List<Employee> employeeList) {
        Optional<Employee> youngestMaleEmployeeInProductDevelopmentWrapper=
                employeeList.stream()
                        .filter(e -> e.getGender()=="Male" && e.getDepartment()=="Product Development")
                        .min(Comparator.comparingInt(Employee::getAge));

        Employee youngestMaleEmployeeInProductDevelopment = youngestMaleEmployeeInProductDevelopmentWrapper.get();

        System.out.println("Details Of Youngest Male Employee In Product Development");

        System.out.println("----------------------------------------------");

        System.out.println("ID : "+youngestMaleEmployeeInProductDevelopment.getId());

        System.out.println("Name : "+youngestMaleEmployeeInProductDevelopment.getName());

        System.out.println("Age : "+youngestMaleEmployeeInProductDevelopment.getAge());

        System.out.println("Year Of Joinging : "+youngestMaleEmployeeInProductDevelopment.getYearOfJoining());

        System.out.println("Salary : "+youngestMaleEmployeeInProductDevelopment.getSalary());
    }

    public static void mostWorkingExperiencedEmployee(List<Employee> employeeList) {
        Optional<Employee> mostWorkingExperiencedEmp=
                employeeList.stream()
                        .sorted(Comparator.comparingLong(Employee::getYearOfJoining)).findFirst();

        Employee mostWorkingExpEmp = mostWorkingExperiencedEmp.get();

        System.out.println("Details Of Youngest Male Employee In Product Development");

        System.out.println("----------------------------------------------");

        System.out.println("ID : "+mostWorkingExpEmp.getId());

        System.out.println("Name : "+mostWorkingExpEmp.getName());

        System.out.println("Age : "+mostWorkingExpEmp.getAge());

        System.out.println("Year Of Joinging : "+mostWorkingExpEmp.getYearOfJoining());

        System.out.println("Salary : "+mostWorkingExpEmp.getSalary());
    }

    public static void countMaleFemaleEmployeesInSalesMarketing(List<Employee> employeeList) {
        Map<String,Long>countMaleFemaleEmployeesInSalesMarketing= employeeList.stream()
                .filter(e -> e.getDepartment().equalsIgnoreCase("Sales And Marketing"))
                .collect(Collectors.groupingBy(Employee::getGender,Collectors.counting()));

        Set<Entry<String,Long>> entrySet=countMaleFemaleEmployeesInSalesMarketing.entrySet();
        for (Entry<String, Long> entry : entrySet)
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }

    public static void avgSalaryOfMaleAndFemaleEmployees(List<Employee> employeeList) {
        Map<String,Double>avgSalaryOfMaleAndFemaleEmployees= employeeList.stream()
                .collect(Collectors.groupingBy(Employee::getGender,Collectors.averagingDouble(Employee::getSalary)));

        Set<Entry<String,Double>> entrySet=avgSalaryOfMaleAndFemaleEmployees.entrySet();
        for (Entry<String, Double> entry : entrySet)
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }

    public static void employeeListByDepartment(List<Employee> employeeList) {
        Map<String,List<Employee>>employeeListByDepartment= employeeList.stream()
                .collect(Collectors.groupingBy(Employee::getDepartment));

        Set<Entry<String,List<Employee>>> entrySet=employeeListByDepartment.entrySet();
        for (Entry<String, List<Employee>> entry : entrySet)
        {
            System.out.println("--------------------------------------");

            System.out.println("Employees In "+entry.getKey() + " : ");

            System.out.println("--------------------------------------");

            List<Employee> list = entry.getValue();

            for (Employee e : list)
            {
                System.out.println(e.getName());
            }
        }
    }

    public static void employeeSalaryStatistics(List<Employee> employeeList) {
        DoubleSummaryStatistics employeeSalaryStatistics=
                employeeList.stream().collect(Collectors.summarizingDouble(Employee::getSalary));

        System.out.println("Average Salary = "+employeeSalaryStatistics.getAverage());

        System.out.println("Total Salary = "+employeeSalaryStatistics.getSum());

        System.out.println("Total Salary = "+employeeSalaryStatistics.getCount());

        System.out.println("Total Salary = "+employeeSalaryStatistics.getMax());

        System.out.println("Total Salary = "+employeeSalaryStatistics.getMin());

        System.out.println("Total Salary = "+employeeSalaryStatistics.getClass());

    }

    public static void partitionEmployeesByAge(List<Employee> employeeList) {
        Map<Boolean,List<Employee>>partitionEmployeesByAge= employeeList.stream()
                .collect(Collectors.partitioningBy(e->e.getAge()>25));

        Set<Entry<Boolean, List<Employee>>> entrySet = partitionEmployeesByAge.entrySet();

        for (Entry<Boolean, List<Employee>> entry : entrySet)
        {
            System.out.println("----------------------------");

            if (entry.getKey())
            {
                System.out.println("Employees older than 25 years :");
            }
            else
            {
                System.out.println("Employees younger than or equal to 25 years :");
            }

            System.out.println("----------------------------");

            List<Employee> list = entry.getValue();

            for (Employee e : list)
            {
                System.out.println(e.getName());
            }
        }
    }

    public static void oldestEmployeeWrapper(List<Employee> employeeList) {
        Optional<Employee> oldestEmployeeWrapper = employeeList.stream().max(Comparator.comparingInt(Employee::getAge));

        Employee oldestEmployee = oldestEmployeeWrapper.get();

        System.out.println("Name : "+oldestEmployee.getName());

        System.out.println("Age : "+oldestEmployee.getAge());

        System.out.println("Department : "+oldestEmployee.getDepartment());
    }
}
```

## Functional Interface

```java
package FunctionalInterface;

import java.util.ArrayList;
import java.util.List;

class Student
{
    int id;

    String name;

    double percentage;

    String specialization;

    public Student(int id, String name, double percentage, String specialization)
    {
        this.id = id;

        this.name = name;

        this.percentage = percentage;

        this.specialization = specialization;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public double getPercentage() {
        return percentage;
    }

    public String getSpecialization() {
        return specialization;
    }

    @Override
    public String toString()
    {
        return id+"-"+name+"-"+percentage+"-"+specialization;
    }
}
public class FunctionalInterface {
    public static void main(String args){

        List<Student> listOfStudents = new ArrayList<Student>();

        listOfStudents.add(new Student(111, "John", 81.0, "Mathematics"));

        listOfStudents.add(new Student(222, "Harsha", 79.5, "History"));

        listOfStudents.add(new Student(333, "Ruth", 87.2, "Computers"));

        listOfStudents.add(new Student(444, "Aroma", 63.2, "Mathematics"));

        listOfStudents.add(new Student(555, "Zade", 83.5, "Computers"));

        listOfStudents.add(new Student(666, "Xing", 58.5, "Geography"));

        listOfStudents.add(new Student(777, "Richards", 72.6, "Banking"));

        listOfStudents.add(new Student(888, "Sunil", 86.7, "History"));

        listOfStudents.add(new Student(999, "Jordan", 58.6, "Finance"));

        listOfStudents.add(new Student(101010, "Chris", 89.8, "Computers"));

        //For example,
        //Imagine an operation where you want only a list of “Mathematics” students from the above listOfStudents. Let’s see how to do it using Predicate.
        //Lambda expression implementing Predicate : Checking specialization of a Student

    }
}
```

## Merge Two Maps

### Java8MergeTwoMaps

```java
package mergeTwoMaps;

import java.util.HashMap;
 
public class Java8MergeTwoMaps 
{
    public static void main(String[] args) 
    {
        //Map-1
         
        HashMap<String, Integer> subjectToStudentCountMap1 = new HashMap<>();
         
        subjectToStudentCountMap1.put("Maths", 45);
        subjectToStudentCountMap1.put("Physics", 57);
        subjectToStudentCountMap1.put("Chemistry", 52);
        subjectToStudentCountMap1.put("History", 41);
         
        //Map-2
         
        HashMap<String, Integer> subjectToStudentCountMap2 = new HashMap<>();
         
        subjectToStudentCountMap2.put("Economics", 49);
        subjectToStudentCountMap2.put("Maths", 42);
        subjectToStudentCountMap2.put("Biology", 41);
        subjectToStudentCountMap2.put("History", 55);
         
        //Merging Map-1 and Map-2 into Map-3
        //If any two keys are found same, their values are added
         
        HashMap<String, Integer> subjectToStudentCountMap3 = new HashMap<>(subjectToStudentCountMap1);
         
        subjectToStudentCountMap2.forEach((key, value) -> subjectToStudentCountMap3.merge(key, value, (v1, v2) -> v1+v2));
         
        //Printing map1, map2 and map3
         
        System.out.println("Map 1 : "+subjectToStudentCountMap1);
         
        System.out.println("Map 2 : "+subjectToStudentCountMap2);
         
        System.out.println("Map 3 : "+subjectToStudentCountMap3);
    }
}
```

### Java8MergeTwoMapsConcat

```java
package mergeTwoMaps;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.stream.Collectors;
import java.util.stream.Stream;
 
public class Java8MergeTwoMapsConcat 
{
    public static void main(String[] args) 
    {
        //Map-1
         
        HashMap<String, Integer> subjectToStudentCountMap1 = new HashMap<>();
         
        subjectToStudentCountMap1.put("Maths", 45);
        subjectToStudentCountMap1.put("Physics", 57);
        subjectToStudentCountMap1.put("Chemistry", 52);
        subjectToStudentCountMap1.put("History", 41);
         
        //Map-2
         
        HashMap<String, Integer> subjectToStudentCountMap2 = new HashMap<>();
         
        subjectToStudentCountMap2.put("Economics", 49);
        subjectToStudentCountMap2.put("Maths", 42);
        subjectToStudentCountMap2.put("Biology", 41);
        subjectToStudentCountMap2.put("History", 55);
         
        //Merging Map-1 and Map-2 into Map-3
        //If any two keys are found same, largest value will be selected
         
        HashMap<String, Integer> subjectToStudentCountMap3 = 
                Stream.concat(subjectToStudentCountMap1.entrySet().stream(), subjectToStudentCountMap2.entrySet().stream())
                      .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (v1, v2) -> v1>v2 ? v1 : v2, HashMap::new));
         
        //Printing map1, map2 and map3
         
        System.out.println("Map 1 : "+subjectToStudentCountMap1);
         
        System.out.println("Map 2 : "+subjectToStudentCountMap2);
         
        System.out.println("Map 3 : "+subjectToStudentCountMap3);
    }
}
```

### Java8MergeTwoMapsOfAndFlatMap

```java
package mergeTwoMaps;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.stream.Collectors;
import java.util.stream.Stream;
 
public class Java8MergeTwoMapsOfAndFlatMap
{
    public static void main(String[] args) 
    {
        //Map-1
         
        HashMap<String, Integer> subjectToStudentCountMap1 = new HashMap<>();
         
        subjectToStudentCountMap1.put("Maths", 45);
        subjectToStudentCountMap1.put("Physics", 57);
        subjectToStudentCountMap1.put("Chemistry", 52);
        subjectToStudentCountMap1.put("History", 41);
         
        //Map-2
         
        HashMap<String, Integer> subjectToStudentCountMap2 = new HashMap<>();
         
        subjectToStudentCountMap2.put("Economics", 49);
        subjectToStudentCountMap2.put("Maths", 42);
        subjectToStudentCountMap2.put("Biology", 41);
        subjectToStudentCountMap2.put("History", 55);
         
        //Merging Map-1 and Map-2 into Map-3
        //If any two keys are found same, their values are added using method reference : Integer::sum
         
        HashMap<String, Integer> subjectToStudentCountMap3 = 
                Stream.of(subjectToStudentCountMap1, subjectToStudentCountMap2)
                      .flatMap(map -> map.entrySet().stream())
                      .collect(Collectors.toMap(Entry::getKey, Entry::getValue, Integer::sum, HashMap::new));
         
        //Printing map1, map2 and map3
         
        System.out.println("Map 1 : "+subjectToStudentCountMap1);
         
        System.out.println("Map 2 : "+subjectToStudentCountMap2);
         
        System.out.println("Map 3 : "+subjectToStudentCountMap3);
    }
}
```

### Java8MergeTwoMapsPilpline

```java
package mergeTwoMaps;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class Java8MergeTwoMapsPilpline 
{
    public static void main(String[] args) 
    {
        //Map-1
         
        HashMap<String, Integer> subjectToStudentCountMap1 = new HashMap<>();
         
        subjectToStudentCountMap1.put("Maths", 45);
        subjectToStudentCountMap1.put("Physics", 57);
        subjectToStudentCountMap1.put("Chemistry", 52);
        subjectToStudentCountMap1.put("History", 41);
         
        //Map-2
         
        HashMap<String, Integer> subjectToStudentCountMap2 = new HashMap<>();
         
        subjectToStudentCountMap2.put("Economics", 49);
        subjectToStudentCountMap2.put("Maths", 42);
        subjectToStudentCountMap2.put("Biology", 41);
        subjectToStudentCountMap2.put("History", 55);
         
        //Merging Map-1 and Map-2 into Map-3
        //If any two keys are found same, smallest value is selected
         
        HashMap<String, Integer> subjectToStudentCountMap3 = 
                subjectToStudentCountMap2.entrySet()
                                         .stream()
                                         .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (v1, v2) -> v1<v2 ? v1 : v2, () -> new HashMap<>(subjectToStudentCountMap1)));
         
        //Printing map1, map2 and map3
         
        System.out.println("Map 1 : "+subjectToStudentCountMap1);
         
        System.out.println("Map 2 : "+subjectToStudentCountMap2);
         
        System.out.println("Map 3 : "+subjectToStudentCountMap3);
    }
}
```

## methodReference

### ConstructorReference

```java
package methodReference;

interface Messageable{
    Message getMessage(String msg);  
}  
class Message{  
    Message(String msg){  
        System.out.print(msg);  
    }  
}  
public class ConstructorReference {  
    public static void main(String[] args) {  
        Messageable hello = Message::new;  
        hello.getMessage("Hello");  
    }  
}  

```

### InstanceMethodReference

```java
package methodReference;

interface Sayable1{
    void say();  
}  
public class InstanceMethodReference {  
    public void saySomething(){  
        System.out.println("Hello, this is non-static method.");  
    }  
    public static void main(String[] args) {  
        InstanceMethodReference methodReference = new InstanceMethodReference(); // Creating object  
        // Referring non-static method using reference  
            Sayable1 sayable = methodReference::saySomething;
        // Calling interface method  
            sayable.say();  
            // Referring non-static method using anonymous object  
            Sayable1 sayable2 = new InstanceMethodReference()::saySomething; // You can use anonymous object also
            // Calling interface method  
            sayable2.say();  
    }  
}  
```

### InstanceMethodReference2

```java
package methodReference;

public class InstanceMethodReference2 {
    public void printnMsg(){  
        System.out.println("Hello, this is instance method");  
    }  
    public static void main(String[] args) {  
    Thread t2=new Thread(new InstanceMethodReference2()::printnMsg);  
        t2.start();       
    }  
}  
```

### InstanceMethodReference3

```java
package methodReference;

import java.util.function.BiFunction;
class Arithmetic2{
public int add(int a, int b){  
return a+b;  
}  
}  
public class InstanceMethodReference3 {  
    public static void main(String[] args) {
        BiFunction<Integer, Integer, Integer>adder = new Arithmetic2()::add;
        int result = adder.apply(10, 20);
        System.out.println(result);
    }
}  
```

### MethodReference

```java
package methodReference;

interface Sayable{
    void say();  
}  
public class MethodReference {  
    public static void saySomething(){  
        System.out.println("Hello, this is static method.");  
    }  
    public static void main(String[] args) {  
        // Referring static method  
        Sayable sayable = MethodReference::saySomething;  
        // Calling interface method  
        sayable.say();  
    }  
}  
```

### MethodReference2

```java
package methodReference;

public class MethodReference2 {
    public static void ThreadStatus(){  
        System.out.println("Thread is running...");  
    }  
    public static void main(String[] args) {  
        Thread t2=new Thread(MethodReference2::ThreadStatus);  
        t2.start();       
    }  
}  
```

## MethodReference3

```java
package methodReference;

import java.util.function.BiFunction;
class Arithmetic1{
    public static int add(int a, int b){
        return a+b;
    }
}  
public class MethodReference3 {  
    public static void main(String[] args) {
        BiFunction<Integer, Integer, Integer>adder = Arithmetic1::add;
        int result = adder.apply(10, 20);
        System.out.println(result);
    }
}  
```

### MethodReference4

```java
package methodReference;

import java.util.function.BiFunction;
class Arithmetic{  
    public static int add(int a, int b){
        return a+b;
    }
    public static float add(int a, float b){
        return a+b;
    }
    public static float add(float a, float b){
        return a+b;
    }
}  
public class MethodReference4 {  
    public static void main(String[] args) {
        BiFunction<Integer, Integer, Integer>adder1 = Arithmetic::add;
        BiFunction<Integer, Float, Float>adder2 = Arithmetic::add;
        BiFunction<Float, Float, Float>adder3 = Arithmetic::add;
        int result1 = adder1.apply(10, 20);
        float result2 = adder2.apply(10, 20.0f);
        float result3 = adder3.apply(10.0f, 20.0f);
        System.out.println(result1);
        System.out.println(result2);
        System.out.println(result3);

    }
} 
```

## countOfFruits

```java
package pr_client;

import java.math.BigDecimal;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

class Item{
    int itemQuantity;
    String itemName;
    BigDecimal itemPrice;
    public Item(String itemName, int itemQuantity, BigDecimal itemPrice){
        this.itemQuantity=itemQuantity;
        this.itemName=itemName;
        this.itemPrice=itemPrice;
    }

    public int getItemQuantity() {
        return itemQuantity;
    }

    public String getItemName() {
        return itemName;
    }

    public BigDecimal getItemPrice() {
        return itemPrice;
    }
}

class Fruits{
    public static void main(String args[]){
        List<Item> items = Arrays.asList(
                new Item("apple", 10, new BigDecimal("9.99")),

                new Item("banana", 20, new BigDecimal("19.99")),

                new Item("orang", 10, new BigDecimal("29.99")),

                new Item("watermelon", 10, new BigDecimal("29.99")),

                new Item("papaya", 20, new BigDecimal("9.99")),

                new Item("apple", 10, new BigDecimal("9.99")),

                new Item("banana", 10, new BigDecimal("19.99")),

                new Item("apple", 20, new BigDecimal("9.99"))
        );
        countOfFruits(items);
    }

    public static void countOfFruits(List<Item> items) {
        System.out.println(items.stream()
                .collect(Collectors.groupingBy(Item::getItemName, Collectors.summingInt(Item::getItemQuantity)))
        );
    }
}
```

## StreamExamples

```java
package pr_client;

import java.util.Comparator;
import java.util.HashMap;
import java.util.Map;
import java.util.stream.Collectors;

class Employee {
    Integer empId;
    String empName;
    Long salary;
    String email;
    Department department;

    Employee(Integer empId,
             String empName,
             Long salary,
             String email,
             Department department) {
        this.empId = empId;
        this.empName = empName;
        this.salary = salary;
        this.email = email;
        this.department = department;
    }

    public Integer getEmpId() {
        return empId;
    }

    public void setEmpId(Integer empId) {
        this.empId = empId;
    }

    public String getEmpName() {
        return empName;
    }

    public void setEmpName(String empName) {
        this.empName = empName;
    }

    public Long getSalary() {
        return salary;
    }

    public void setSalary(Long salary) {
        this.salary = salary;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public Department getDepartment() {
        return department;
    }

    public void setDepartment(Department department) {
        this.department = department;
    }
}


class Department {
    Integer deptId;
    String departmentName;

    Department(Integer deptId,
               String departmentName) {
        this.deptId = deptId;
        this.departmentName = departmentName;
    }

    public Integer getDeptId() {
        return deptId;
    }

    public void setDeptId(Integer deptId) {
        this.deptId = deptId;
    }

    public String getDepartmentName() {
        return departmentName;
    }

    public void setDepartmentName(String departmentName) {
        this.departmentName = departmentName;
    }
}

public class StreamExamples {

    public static void main(String args[]) {
        Department hrDept = new Department(1, "HR");
        Department corpDept = new Department(2, "CORP");
        Department itDept = new Department(3, "IT");
        Department markDept = new Department(3, "MKT");
        Map<Integer, Employee> empMap = new HashMap<>();
        empMap.put(1, new Employee(1, "Harsh", 1000L, "Harsh@gmail.com", hrDept));
        empMap.put(2, new Employee(2, "Harshita", 2000L, "Harshitha@gmail.com", hrDept));
        empMap.put(3, new Employee(3, "Harshad", 1000L, "Harshad@gmail.com", hrDept));
        empMap.put(4, new Employee(4, "Harshneeta", 4000L, "Harshneeta@gmail.com", hrDept));
        empMap.put(5, new Employee(5, "Harshal", 2000L, "Harshal@gmail.com", hrDept));
        empMap.put(6, new Employee(6, "Harshali", 3000L, "Harshali@gmail.com", hrDept));
        empMap.put(11, new Employee(11, "Harshi", 1000L, "Harsh@gmail.com", corpDept));
        empMap.put(12, new Employee(12, "Harshita", 2000L, "Harshitha@gmail.com", corpDept));
        empMap.put(13, new Employee(13, "Harshad", 1000L, "Harshad@gmail.com", corpDept));
        empMap.put(14, new Employee(14, "Harshneeta", 4000L, "Harshneeta@gmail.com", itDept));
        empMap.put(15, new Employee(15, "Harshal", 2000L, "Harshal@gmail.com", itDept));
        empMap.put(16, new Employee(16, "Harshali", 3000L, "Harshali@gmail.com", itDept));
        highestSalaryInEachDepartment(empMap);
        salaryListForHRDept(empMap);
        salaryListForAllDept(empMap);
    }

    // Find the  highest salary paid  in each department for all departments
    public static void highestSalaryInEachDepartment(Map<Integer, Employee> empMap) {
        empMap.values().stream()
                .collect(Collectors.groupingBy(Employee::getDepartment,
                        Collectors.maxBy(Comparator.comparing(Employee::getSalary))))
                .forEach((k, v) -> System.out.println("Highest salary in " + k.departmentName + " is " + v.get().getSalary()));

    }

    // Find the salary list sorted for employees HR department in desc order without duplicates from the Map<Integer,Employee>
    public static void salaryListForHRDept(Map<Integer, Employee> empMap) {
        System.out.println("HR Salaries:" + empMap.values().stream().filter(employee ->
                "HR".equals(employee.getDepartment().getDepartmentName()))
                .map(employee -> employee.getSalary()).distinct().sorted(Comparator.reverseOrder())
                .collect(Collectors.toList()));
    }

    // Find the salary list for employees all department in desc order without duplicates from the Map<Integer,Employee>
    public static void salaryListForAllDept(Map<Integer, Employee> empMap) {
        System.out.println(empMap.values().stream().collect(Collectors.groupingBy(employee ->
                employee.getDepartment().getDepartmentName(),
                Collectors.mapping(Employee::getSalary, Collectors.toSet()))));
        ;
    }
}

```

## synchronization

### DeadLockInJava

```java
package synchronization;

class Shareds
{
    synchronized void methodOne(Shareds s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodOne...");
 
        System.out.println(t.getName()+"is calling methodTwo...");
 
        s.methodTwo(this);
 
        System.out.println(t.getName()+"is finished executing methodOne...");
    }
 
    synchronized void methodTwo(Shareds s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodTwo...");
 
        System.out.println(t.getName()+"is calling methodOne...");
 
        s.methodOne(this);
 
        System.out.println(t.getName()+"is finished executing methodTwo...");
    }
}
 
public class DeadLockInJava
{
    public static void main(String[] args)
    {
        final Shareds s1 = new Shareds();
 
        final Shareds s2 = new Shareds();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s1.methodOne(s2);
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s2.methodTwo(s1);
            }
        };
 
        t1.start();
 
        t2.start();
    }
}
```

### DeadlockThreadsInJava

```java
package synchronization;

import java.lang.management.ManagementFactory;
import java.lang.management.ThreadInfo;
import java.lang.management.ThreadMXBean;
 
class Shared1
{
    synchronized void methodOne(Shared1 s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodOne...");
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        System.out.println(t.getName()+"is calling methodTwo...");
 
        s.methodTwo(this);
 
        System.out.println(t.getName()+"is finished executing methodOne...");
    }
 
    synchronized void methodTwo(Shared1 s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodTwo...");
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        System.out.println(t.getName()+"is calling methodOne...");
 
        s.methodOne(this);
 
        System.out.println(t.getName()+"is finished executing methodTwo...");
    }
}
 
public class DeadlockThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared1 s1 = new Shared1();
 
        final Shared1 s2 = new Shared1();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s1.methodOne(s2);
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s2.methodTwo(s1);
            }
        };
 
        t1.start();
 
        t2.start();
 
        try
        {
            Thread.sleep(5000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        ThreadMXBean bean = ManagementFactory.getThreadMXBean();
 
        long ids[] = bean.findMonitorDeadlockedThreads();
 
        if(ids != null)
        {
            ThreadInfo threadInfo[] = bean.getThreadInfo(ids);
 
            for (ThreadInfo threadInfo1 : threadInfo)
            {
                System.out.println(threadInfo1.getThreadId());    //Prints the ID of deadlocked thread
 
                System.out.println(threadInfo1.getThreadName());  //Prints the name of deadlocked thread
 
                System.out.println(threadInfo1.getLockName());    //Prints the string representation of an object for which thread has entered into deadlock.
 
                System.out.println(threadInfo1.getLockOwnerId());  //Prints the ID of thread which currently owns the object lock
 
                System.out.println(threadInfo1.getLockOwnerName());  //Prints name of the thread which currently owns the object lock.
            }
        }
        else
        {
            System.out.println("No Deadlocked Threads");
        }
    }
}
```

### JavaThreadLifeCycle

```java

package synchronization;

public class JavaThreadLifeCycle
{
    public static void main(String[] args)
    {
        Thread t = new Thread();
 
        //Checking the state before starting the thread
 
        System.out.println(t.getState());     //Output : NEW
    }
}
```

### JavaThreadLifeCycleRunnable

```java
package synchronization;

public class JavaThreadLifeCycleRunnable {
    public static void main(String[] args) {
        Thread t = new Thread();

        t.start();

        //Checking the state after starting the thread

        System.out.println(t.getState());     //Output : RUNNABLE
    }
}
```

### Odd Even Thread

```java
package synchronization;//OddThread to print odd numbers
//Calls printOdd() method of SharedPrinter class until limit is exceeded.
 
class OddThread extends Thread
{
    int limit;
     
    sharedPrinter printer;
     
    public OddThread(int limit, sharedPrinter printer)
    {
        this.limit = limit;
         
        this.printer = printer;
    }
     
    @Override
    public void run() 
    {
        int oddNumber = 1;        //First odd number is 1
         
        while (oddNumber <= limit)
        {
            printer.printOdd(oddNumber);       //Calling printOdd() method of SharedPrinter class
             
            oddNumber = oddNumber + 2;         //Incrementing to next odd number
        }
    }
}
 
//EvenThread to print even numbers.
//Calls printEven() method of SharedPrinter class until limit is exceeded.
 
class EvenThread extends Thread
{
    int limit;
     
    sharedPrinter printer;
     
    public EvenThread(int limit, sharedPrinter printer)
    {
        this.limit = limit;
         
        this.printer = printer;
    }
     
    @Override
    public void run() 
    {
        int evenNumber = 2;           //First even number is 2
         
        while (evenNumber <= limit)
        {
            printer.printEven(evenNumber);          //Calling printEven() method of SharedPrinter class
             
            evenNumber = evenNumber + 2;           //Incrementing to next even number
        }
    }
}
 
class sharedPrinter
{
    //A boolean flag variable to check whether odd number is printed or not
    //Initially it is false.
     
    boolean isOddPrinted = false;
     
    //synchronized printOdd() method to print odd numbers. It is executed by OddThread.
    //First checks isOddPrinted, 
    //if isOddPrinted is true then it waits until next even number is printed by EvenThread
    //If isOddPrinted is false then prints next odd number, sets isOddPrinted to true
    //sleeps for 1 second before notifying EvenThread
     
    synchronized void printOdd(int number)
    {
        while (isOddPrinted)
        {
            try
            {
                wait();
            } 
            catch (InterruptedException e)
            {
                e.printStackTrace();
            }
        }
         
        System.out.println(Thread.currentThread().getName()+" : "+number);
         
        isOddPrinted = true;
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        notify();
    }
     
    //Synchronized printEven() method to print even numbers. It is executed by EvenThread.
    //First checks isOddPrinted, 
    //if isOddPrinted is false then it waits until next odd number is printed by OddThread
    //If isOddPrinted is true then it prints next even number, sets isOddPrinted to false
    //sleeps for 1 second before notifying OddThread
     
    synchronized void printEven(int number)
    {
        while (! isOddPrinted)
        {
            try
            {
                wait();
            }
            catch (InterruptedException e) 
            {
                e.printStackTrace();
            }
        }
         
        System.out.println(Thread.currentThread().getName()+" : "+number);
         
        isOddPrinted = false;
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        notify();
    }
}
 
//Main Class
 
public class MainClass 
{
    public static void main(String[] args) 
    {
        sharedPrinter printer = new sharedPrinter();
         
        OddThread oddThread = new OddThread(20, printer);
         
        oddThread.setName("Odd-Thread");
         
        EvenThread evenThread = new EvenThread(20, printer);
         
        evenThread.setName("Even-Thread");
         
        oddThread.start();
         
        evenThread.start();
    }
}
```

### ThreadsInJava

```java
package synchronization;

class Shared
{
    int i;
 
    synchronized void SharedMethod()
    {
        Thread t = Thread.currentThread();
 
        for(i = 0; i <= 1000; i++)
        {
            System.out.println(t.getName()+" : "+i);
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared s1 = new Shared();
 
        Thread t1 = new Thread("Thread - 1")
        {
            @Override
            public void run()
            {
                s1.SharedMethod();
            }
        };
 
        Thread t2 = new Thread("Thread - 2")
        {
            @Override
            public void run()
            {
                s1.SharedMethod();
            }
        };
 
        t1.start();
 
        t2.start();
    }
}
```

### ThreadsInJavaBlocked

```java
package synchronization;

class Shared2
{
    synchronized void methodOne(Shared2 s)
    {
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        s.methodTwo(this);
    }
 
    synchronized void methodTwo(Shared2 s)
    {
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        s.methodOne(this);
    }
}
 
public class ThreadsInJavaBlocked
{
    public static void main(String[] args)
    {
        final Shared2 s1 = new Shared2();
 
        final Shared2 s2 = new Shared2();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s1.methodOne(s2);
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s2.methodTwo(s1);
            }
        };
 
        t1.start();
 
        t2.start();
 
        try
        {
            Thread.sleep(3000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking states of both the threads
 
        System.out.println(t1.getState());     //Output : BLOCKED
 
        System.out.println(t2.getState());     //Output : BLOCKED
    }
}
```

### ThreadsInJavaSleepOrWaitOrJoin

```java
package synchronization;

public class ThreadsInJavaSleepOrWaitOrJoin
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t.start();
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking the state when thread is sleeping
 
        System.out.println(t.getState());     //Output : TIMED_WAITING
    }
}
```

### ThreadsInJavaTerminated

```java

package synchronization;

public class ThreadsInJavaTerminated
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                for(int i = 0; i <= 25; i++)
                {
                    System.out.println(i);
                }
            }
        };
 
        t.start();
 
        try
        {
            Thread.sleep(2000);      //Main thread is sleeping for 2 sec
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking the state when thread t is finished it's execution
 
        System.out.println(t.getState());     //Output : TERMINATED
    }
}
```

### ThreadsInJavaWaitOrJoin

```java
package synchronization;

public class ThreadsInJavaWaitOrJoin
{
    public static void main(String[] args)
    {
        final Thread t1 = new Thread()
        {
            public void run()
            {
                try
                {
                    Thread.sleep(2000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        Thread t2 = new Thread()
        {
            public void run()
            {
                try
                {
                    t1.join();
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t2.start();
 
        t1.start();
 
        try
        {
            Thread.sleep(100);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking the state of t2 after it calls join() on t1
 
        System.out.println(t2.getState());     //Output : WAITING
    }
}
```

### ThreadsStatesInJava

```java
package synchronization;

public class ThreadsStatesInJava
{
    public static void main(String[] args)
    {
        Thread.State[] states = Thread.State.values();
 
        for (Thread.State state : states)
        {
            System.out.println(state);
        }
    }
}
```

## FutureExample

```java
package future;

import java.util.concurrent.*;
public class FutureExample {
    public static void main(String args[]) throws InterruptedException, ExecutionException
    {
        //ExecutorService allows us to execute tasks on threads asynchronously
        ExecutorService es = Executors.newSingleThreadExecutor();
        //getting future
        //the method submit() submits a value-returning task for execution and returns the Future
        Future<String> future = es.submit(() ->
        {
            //sleep thread for 2 seconds
            Thread.sleep(2000);
            return "Welcome to Javatpoint";
        });
        //checks if the task is completed or not
        while(!future.isDone())
        {
            System.out.println("The task is still in process.....");
            //sleep thread for 2 milliseconds
            Thread.sleep(200);
        }
        System.out.println("Task completed! getting the result");
        //getting the result after completing the task
        String result = future.get();
        //prints the result
        System.out.println(result);
        es.shutdown();
    }
} 
```

## ExecutorService

### ParallelRequestSender

```java
package ExecutorService;

import java.util.concurrent.*;

public class ParallelRequestSender {
    public static void main(String[] args) {
        // Number of parallel requests
        int numberOfRequests = 10;

        // Limit the number of concurrent requests to 3
        int maxConcurrentRequests = 3;

        // Create an ExecutorService with a fixed thread pool
        ExecutorService executorService = Executors.newFixedThreadPool(maxConcurrentRequests);

        // Create a CompletionService to manage the completion of tasks
        CompletionService<String> completionService = new ExecutorCompletionService<>(executorService);

        // Send parallel requests
        for (int i = 0; i < numberOfRequests; i++) {
            final int requestId = i;
            completionService.submit(() -> {
                // Your request logic here
                // For example, simulate a request by sleeping for a random duration
                Thread.sleep((long) (Math.random() * 1000));
                return "Request " + requestId + " completed";
            });
        }

        // Retrieve results as they become available
        for (int i = 0; i < numberOfRequests; i++) {
            try {
                Future<String> completedTask = completionService.take();
                String result = completedTask.get();
                System.out.println(result);
            } catch (InterruptedException | ExecutionException e) {
                e.printStackTrace();
            }
        }

        // Shutdown the executor service
        executorService.shutdown();
    }
}
```

### ParallelRequestSenderCmpletable

```java
package ExecutorService;

import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class ParallelRequestSenderCmpletable {
    public static void main(String[] args) {
        // Number of parallel requests
        int numberOfRequests = 10;

        // Limit the number of concurrent requests to 3
        int maxConcurrentRequests = 3;

        // Create a list of CompletableFuture to represent the parallel requests
        List<CompletableFuture<String>> futures = IntStream.range(0, numberOfRequests)
                .mapToObj(i -> CompletableFuture.supplyAsync(() -> {
                    // Your request logic here
                    // For example, simulate a request by sleeping for a random duration
                    try {
                        Thread.sleep((long) (Math.random() * 1000));
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    return "Request " + i + " completed";
                }))
                .collect(Collectors.toList());

        // Limit the concurrency by combining CompletableFuture in chunks
        List<List<CompletableFuture<String>>> chunks = chunkList(futures, maxConcurrentRequests);

        // Combine chunks of CompletableFuture
        List<CompletableFuture<List<String>>> combinedFutures = chunks.stream()
                .map(chunk -> CompletableFuture.allOf(chunk.toArray(new CompletableFuture[0]))
                        .thenApply(v -> chunk.stream()
                                .map(CompletableFuture::join)
                                .collect(Collectors.toList())))
                .collect(Collectors.toList());

        // Combine chunks and flatten the results
        CompletableFuture<List<String>> finalResult = CompletableFuture.allOf(
                combinedFutures.toArray(new CompletableFuture[0])
        ).thenApply(v -> combinedFutures.stream()
                .flatMap(future -> future.join().stream())
                .collect(Collectors.toList()));

        // Join and print the final results
        finalResult.join().forEach(System.out::println);
    }

    private static <T> List<List<T>> chunkList(List<T> list, int chunkSize) {
        return IntStream.range(0, list.size())
                .boxed()
                .collect(Collectors.groupingBy(index -> index / chunkSize))
                .values()
                .stream()
                .map(indices -> indices.stream()
                        .map(list::get)
                        .collect(Collectors.toList()))
                .collect(Collectors.toList());
    }
}

```

## Date

### LocalDateExample3
```java
package date;

import java.time.*;
public class LocalDateExample3 {  
  public static void main(String[] args) {  
    LocalDate date = LocalDate.of(2017, 1, 13);  
    LocalDateTime datetime = date.atTime(1,50,9);      
    System.out.println(datetime);

    //LocalDateTime  ldt = LocalDateTime.of(2017, Month.JANUARY,  19,   15,   26);
    ZoneId  india = ZoneId.of("Asia/Kolkata");
    ZonedDateTime zone1  = ZonedDateTime.of(datetime, india);
    System.out.println("In India Central Time Zone: " + zone1);

  }  
}  
```

### LocalDateExample4

```java
package date;

import java.time.LocalDate;
import java.time.format.DateTimeFormatter;  
public class LocalDateExample4  
{  
    public static void main(String ar[])  
    {  
        // Converting LocalDate to String  
        // Example 1  
        LocalDate d1 = LocalDate.now();  
        String d1Str = d1.format(DateTimeFormatter.ISO_DATE);  
        System.out.println("Date1 in string :  " + d1Str);  
        // Example 2  
        LocalDate d2 = LocalDate.of(2002, 05, 01);  
        String d2Str = d2.format(DateTimeFormatter.ISO_DATE);  
        System.out.println("Date2 in string :  " + d2Str);  
        // Example 3  
        LocalDate d3 = LocalDate.of(2016, 11, 01);  
        String d3Str = d3.format(DateTimeFormatter.ISO_DATE);  
        System.out.println("Date3 in string :  " + d3Str);  
    }  
}  
```

## Sorting

### ListSorting

```java
package CoreQuestion.sort;

import java.util.ArrayList;
import java.util.Collections;
 
public class ListSorting 
{       
    public static void main(String[] args) 
    {
        //Creating an ArrayList of strings
         
        ArrayList<String> list = new ArrayList<String>();
         
        //Adding elements to list
         
        list.add("Virat");
         
        list.add("rohit");
         
        list.add("Shikar");
         
        list.add("ashwin");
         
        list.add("ravindra");
         
        list.add("Bhargav");
         
        System.out.println("ArrayList Before Sorting :");
         
        System.out.println(list);
         
        //Sorting the list
         
        Collections.sort(list);
         
        System.out.println("ArrayList After Sorting :");
         
        System.out.println(list);
    }   
}
```

### ListSortingTWO

```java
package CoreQuestion.sort;

import java.util.ArrayList;
import java.util.Collections;
 
public class ListSortingTWO 
{       
    public static void main(String[] args) 
    {
        //Creating an ArrayList of strings
         
        ArrayList<String> list = new ArrayList<String>();
         
        //Adding elements to list
         
        list.add("Virat");
         
        list.add("rohit");
         
        list.add("Shikar");
         
        list.add("ashwin");
         
        list.add("ravindra");
         
        list.add("Bhargav");
         
        System.out.println("ArrayList Before Sorting :");
         
        System.out.println(list);
         
        //Sorting the list by ignoring the case
         
        Collections.sort(list, String.CASE_INSENSITIVE_ORDER);
         
        System.out.println("ArrayList After Sorting :");
         
        System.out.println(list);
    }   
}
```

### Student Sorting Programs

```java
package CoreQuestion.sort;

import java.util.ArrayList;
import java.util.Collections;
 
//Student class implementing Comparable interface
 
class Student implements Comparable<Student>
{
    int id;
     
    String name;
     
    int percentage;
     
    public Student(int id, String name, int percentage)
    {
        this.id = id;
         
        this.name = name;
         
        this.percentage = percentage;
    }
     
    @Override
    public int compareTo(Student s)
    {
        return this.id - s.id;     //Sorts the objects in ascending order
         
        // return s.id - this.id;    //Sorts the objects in descending order
    }
     
    @Override
    public String toString()
    {
        return "{ID : "+id+", Name : "+name+", Percentage : "+percentage+"}";
    }
}
 
public class MainClass 
{       
    public static void main(String[] args) 
    {
        //Creating an ArrayList of Student objects
         
        ArrayList<Student> listOfStudents = new ArrayList<Student>();
         
        //Adding students to listOfStudents
         
        listOfStudents.add(new Student(123, "Student1", 62));
         
        listOfStudents.add(new Student(231, "Student2", 81));
         
        listOfStudents.add(new Student(85, "Student3", 79));
         
        listOfStudents.add(new Student(478, "Student4", 94));
         
        listOfStudents.add(new Student(365, "Student5", 62));
         
        System.out.println("listOfStudents Before Sorting :");
         
        System.out.println(listOfStudents);
         
        //Sorting the listOfStudents
         
        Collections.sort(listOfStudents);
         
        System.out.println("listOfStudents After Sorting :");
         
        System.out.println(listOfStudents);
    }   
}
```

### MainClassSecondLargest Number

```java
package CoreQuestion.sort;
//To Find Second Largest Number In An Integer Array
public class MainClassSecondLargest
{
    static int secondLargest(int[] input)
    {
        int firstLargest, secondLargest;
 
        //Checking first two elements of input array
 
        if(input[0] > input[1])
        {
            //If first element is greater than second element
 
            firstLargest = input[0];
 
            secondLargest = input[1];
        }
        else
        {
            //If second element is greater than first element
 
            firstLargest = input[1];
 
            secondLargest = input[0];
        }
 
        //Checking remaining elements of input array
 
        for (int i = 2; i < input.length; i++)
        {
            if(input[i] > firstLargest)
            {
                //If element at 'i' is greater than 'firstLargest'
 
                secondLargest = firstLargest;
 
                firstLargest = input[i];
            }
            else if (input[i] < firstLargest && input[i] > secondLargest)
            {
                //If element at 'i' is smaller than 'firstLargest' and greater than 'secondLargest'
 
                secondLargest = input[i];
            }
        }
 
        return secondLargest;
    }
 
    public static void main(String[] args)
    {
        System.out.println(secondLargest(new int[] {45, 51, 28, 75, 49, 42}));
 
        System.out.println(secondLargest(new int[] {985, 521, 975, 831, 479, 861}));
 
        System.out.println(secondLargest(new int[] {9459, 9575, 5692, 1305, 1942, 9012}));
 
        System.out.println(secondLargest(new int[] {47498, 14526, 74562, 42681, 75283, 45796}));
    }
}
```

### MainClassThree

```java
package CoreQuestion.sort;

import java.util.ArrayList;
import java.util.Collections;
 
public class MainClassThree 
{       
    public static void main(String[] args) 
    {
        //Creating an ArrayList of integers
         
        ArrayList<Integer> list = new ArrayList<Integer>();
         
        //Adding elements to list
         
        list.add(1452);
         
        list.add(6854);
         
        list.add(8741);
         
        list.add(6542);
         
        list.add(3845);
         
        System.out.println("ArrayList Before Sorting :");
         
        System.out.println(list);
         
        //Sorting the list in the reverse order
         
        Collections.sort(list, Collections.reverseOrder());
         
        System.out.println("ArrayList Sorted In The Reverse Order :");
         
        System.out.println(list);
    }   
}
```

### MainClassTwo

```java
package CoreQuestion.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
 
//Students class implementing Comparable interface
 
class Students implements Comparable<Students>
{
    int id;
     
    String name;
     
    int percentage;
     
    public Students(int id, String name, int percentage)
    {
        this.id = id;
         
        this.name = name;
         
        this.percentage = percentage;
    }
     
    @Override
    public int compareTo(Students s)
    {
        return this.id - s.id;     //Sorts the objects in ascending order
         
        // return s.id - this.id;    //Sorts the objects in descending order
    }
     
    @Override
    public String toString()
    {
        return "{ID : "+id+", Name : "+name+", Percentage : "+percentage+"}";
    }
}
 
//Defining our own Comparator
 
class OrderByPercentage implements Comparator<Students>
{
    @Override
    public int compare(Students s1, Students s2)
    {
        return s1.percentage - s2.percentage;
    }
}
 
public class MainClassTwo 
{       
    public static void main(String[] args) 
    {
        //Creating an ArrayList of Students objects
         
        ArrayList<Students> listOfStudentss = new ArrayList<Students>();
         
        //Adding Studentss to listOfStudentss
         
        listOfStudentss.add(new Students(123, "Students1", 62));
         
        listOfStudentss.add(new Students(231, "Students2", 81));
         
        listOfStudentss.add(new Students(85, "Students3", 79));
         
        listOfStudentss.add(new Students(478, "Students4", 94));
         
        listOfStudentss.add(new Students(365, "Students5", 62));
         
        System.out.println("listOfStudentss Before Sorting :");
         
        System.out.println(listOfStudentss);
         
        //Sorting the listOfStudentss by percentage
         
        Collections.sort(listOfStudentss, new OrderByPercentage());
         
        System.out.println("listOfStudentss After Sorting :");
         
        System.out.println(listOfStudentss);
    }   
}
```

### MergeArrayProgram

```java
package CoreQuestion.sort;

import java.util.Arrays;
//Java Program To Merge Two Unsorted Arrays In Sorted Order
public class MergeArrayProgram 
{
    private static int[] mergeArray(int[] arrayA, int[] arrayB) {
        int[] mergedArray = new int[arrayA.length + arrayB.length];

        int i=0, j=0, k=0;

        while (i < arrayA.length) {
            mergedArray[k] = arrayA[i];
            i++;
            k++;
        }

        while (j < arrayB.length) {
            mergedArray[k] = arrayB[j];
            j++;
            k++;
        }

        Arrays.sort(mergedArray);

        return mergedArray;
    }

    public static void main(String[] args) {
        int[] arrayA = new int[] {12, -7, 18, 9, 37, -1, 21};

        int[] arrayB = new int[] {27, 8, 71, -9, 18};

        int[] mergedArray = mergeArray(arrayA, arrayB);

        System.out.println("Array A : "+Arrays.toString(arrayA));

        System.out.println("Array B : "+Arrays.toString(arrayB));

        System.out.println("Merged Array : "+Arrays.toString(mergedArray));
    }
}
```

### MergeArrayProgramTwo

```java
package CoreQuestion.sort;

import java.util.Arrays;
//How To Merge Two Sorted Arrays In Java?
public class MergeArrayProgramTwo 
{
    private static int[] mergeArray(int[] arrayA, int[] arrayB) {
        int[] mergedArray = new int[arrayA.length + arrayB.length];

        int i=0, j=0, k=0;

        while (i < arrayA.length && j < arrayB.length) {
            if (arrayA[i] < arrayB[j]) {
                mergedArray[k] = arrayA[i];
                i++;
                k++;
            } else {
                mergedArray[k] = arrayB[j];
                j++;
                k++;
            }
        }

        while (i < arrayA.length) {
            mergedArray[k] = arrayA[i];
            i++;
            k++;
        }

        while (j < arrayB.length) {
            mergedArray[k] = arrayB[j];
            j++;
            k++;
        }

        return mergedArray;
    }

    public static void main(String[] args) {
        int[] arrayA = new int[] {-7, 12, 17, 29, 41, 56, 79};

        int[] arrayB = new int[] {-9, -3, 0, 5, 19};

        int[] mergedArray = mergeArray(arrayA, arrayB);

        System.out.println("Array A : "+Arrays.toString(arrayA));

        System.out.println("Array B : "+Arrays.toString(arrayB));

        System.out.println("Merged Array : "+Arrays.toString(mergedArray));
    }
}
```

### MergeTwoArraysAndRemoveDuplicatesProgram

```java

package CoreQuestion.sort;

import java.util.Arrays;
import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;
 
public class MergeTwoArraysAndRemoveDuplicatesProgram 
{   
    private static int[] mergeArraysAndRemoveDuplicates(int[] arrayA, int[] arrayB)
    {
        //Step 1 : Merging of two arrays
         
        //Defining mergedArray with combined size of arrayA and arrayB
         
        int[] mergedArray = new int[arrayA.length + arrayB.length];
         
        //Initializing pointers of arrayA, arrayB and mergedArray with 0
         
        int i=0, j=0, k=0;
         
        //Inserting all elements of arrayA into mergedArray
         
        while (i < arrayA.length)
        {
            mergedArray[k] = arrayA[i];
            k++;
            i++;
        }
         
        //Inserting all elements of arrayB into mergedArray
         
        while (j < arrayB.length)
        {
            mergedArray[k] = arrayB[j];
            k++;
            j++;
        }
         
        //Step 2 : Removing duplicates from merged array
         
        //Defining one HashSet object called setWithNoDuplicates
        //Remember, HashSet allows only unique elements
         
        Set<Integer> setWithNoDuplicates = new HashSet<>();
         
        //Adding all elements of mergedArray into setWithNoDuplicates
         
        for (int m = 0; m < mergedArray.length; m++) 
        {
            setWithNoDuplicates.add(mergedArray[m]);
        }
         
        //Now, setWithNoDuplicates will have only unique elements of mergedArray
         
        //So, now iterate setWithNoDuplicates and 
        //add its elements into new array called mergedArrayWithNoDuplicates
         
        Iterator<Integer> it = setWithNoDuplicates.iterator();
         
        int[] mergedArrayWithNoDuplicates = new int[setWithNoDuplicates.size()];
         
        int n = 0;
         
        //Adding all elements of setWithNoDuplicates into mergedArrayWithNoDuplicates
         
        while (it.hasNext()) 
        {
            mergedArrayWithNoDuplicates[n] = it.next();
            n++;
        }
         
        //Step 3 : Sorting merged array after removing duplicates
         
        Arrays.sort(mergedArrayWithNoDuplicates);
         
        return mergedArrayWithNoDuplicates;
    }
     
    public static void main(String[] args)
    {
        int[] arrayA = new int[] {7, -5, 3, 8, -4, 11, -19, 21};
         
        int[] arrayB = new int[] {6, 13, -7, 0, 11, -4, 3, -5};
         
        int[] mergedArray = mergeArraysAndRemoveDuplicates(arrayA, arrayB);
         
        System.out.println("Array A : "+Arrays.toString(arrayA));
         
        System.out.println("Array B : "+Arrays.toString(arrayB));
         
        System.out.println("Sorted Merged Array With No Duplicates : ");
         
        System.out.println(Arrays.toString(mergedArray));
    }
}
```

### MergeTwoArraysAndRemoveDuplicatesProgramTwo

```java

package CoreQuestion.sort;

import java.util.Arrays;
import java.util.stream.IntStream;
 
public class MergeTwoArraysAndRemoveDuplicatesProgramTwo 
{   
    private static int[] mergeArraysAndRemoveDuplicates(int[] arrayA, int[] arrayB)
    {
        return IntStream.concat(IntStream.of(arrayA), IntStream.of(arrayB))
                        .distinct()
                        .sorted()
                        .toArray();
    }
     
    public static void main(String[] args)
    {
        int[] arrayA = new int[] {7, -5, 3, 8, -4, 11, -19, 21};
         
        int[] arrayB = new int[] {6, 13, -7, 0, 11, -4, 3, -5};
         
        int[] mergedArray = mergeArraysAndRemoveDuplicates(arrayA, arrayB);
         
        System.out.println("Array A : "+Arrays.toString(arrayA));
         
        System.out.println("Array B : "+Arrays.toString(arrayB));
         
        System.out.println("Sorted Merged Array With No Duplicates : ");
         
        System.out.println(Arrays.toString(mergedArray));
    }
}

```

## sortMapJava8

### ReverseTheString

```java
package CoreQuestion.sortMapJava8;

public class ReverseTheString
{
    public static void main(String[] args)
    {
        String str = "MyJava";
 
        //1. Using StringBuffer Class
 
        StringBuffer sbf = new StringBuffer(str);
 
        System.out.println(sbf.reverse());    //Output : avaJyM
 
        //2. Using iterative method
 
        char[] strArray = str.toCharArray();
 
        for (int i = strArray.length - 1; i >= 0; i--)
        {
            System.out.print(strArray[i]);    //Output : avaJyM
        }
 
        System.out.println();
 
        //3. Using Recursive Method
 
        System.out.println(recursiveMethod(str));    //Output : avaJyM
    }
 
    //Recursive method to reverse string
 
    static String recursiveMethod(String str)
    {
         if ((null == str) || (str.length() <= 1))
         {
                return str;
         }
 
         return recursiveMethod(str.substring(1)) + str.charAt(0);
    }
}
```

### SortMapByKeysProgram

```java
package CoreQuestion.sortMapJava8;

import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;
 
public class SortMapByKeysProgram
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap = new TreeMap<>(studentMap);
                 
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramEight

```java
package CoreQuestion.sortMapJava8;

import java.util.Collections;
import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByKeysProgramEight
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap 
                                = studentMap.entrySet()
                                            .stream()
                                            .sorted(Entry.comparingByKey((o1, o2) -> o2.length() - o1.length()))
                                                           
                                         //  OR
                                        //  .sorted(Collections.reverseOrder(Entry.comparingByKey((o1, o2) -> o1.length() - o2.length())))
                                             
                                            .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1, e2) -> e2, LinkedHashMap::new));
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramFive

```java
package CoreQuestion.sortMapJava8;

import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByKeysProgramFive
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap 
                    = studentMap.entrySet()
                                .stream()
                                .sorted(Entry.comparingByKey())
                                .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1, e2) -> e2, LinkedHashMap::new));
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramFour

```java
package CoreQuestion.sortMapJava8;

import java.util.Comparator;
import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;
 
public class SortMapByKeysProgramFour
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap = new TreeMap<>(new Comparator<String>() 
        {
            @Override
            public int compare(String o1, String o2) 
            {
                return o2.length() - o1.length();
            }
        });
                 
//      OR
         
//      Map<String, Integer> sortedStudentMap = new TreeMap<>(Collections.reverseOrder(new Comparator<String>() 
//      {
//          @Override
//          public int compare(String o1, String o2) 
//          {
//              return o1.length() - o2.length();
//          }
//      }));
         
        sortedStudentMap.putAll(studentMap);
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramSeven

```java
package CoreQuestion.sortMapJava8;

import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByKeysProgramSeven
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap 
                                = studentMap.entrySet()
                                            .stream()
                                            .sorted(Entry.comparingByKey((o1, o2) -> o1.length() - o2.length()))
                                            .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1, e2) -> e2, LinkedHashMap::new));
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramSix

```java
package CoreQuestion.sortMapJava8;

import java.util.Collections;
import java.util.Comparator;
import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByKeysProgramSix
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap 
                        = studentMap.entrySet()
                                    .stream()
                                    .sorted(Collections.reverseOrder(Entry.comparingByKey()))
                                     
                                //  OR
                                // .sorted(Entry.comparingByKey(Comparator.reverseOrder()))
                                     
                                    .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1, e2) -> e2, LinkedHashMap::new));
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramThree

```java
package CoreQuestion.sortMapJava8;

import java.util.Comparator;
import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;
 
public class SortMapByKeysProgramThree
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap = new TreeMap<>(new Comparator<String>() 
        {
            @Override
            public int compare(String o1, String o2)
            {                                           
                return o1.length() - o2.length();
            }                                   
        });
                 
        sortedStudentMap.putAll(studentMap);
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```

### SortMapByKeysProgramTwo

```java
package CoreQuestion.sortMapJava8;

import java.util.Collections;
import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;
 
public class SortMapByKeysProgramTwo
{
    public static void main(String[] args) 
    {
        Map<String, Integer> studentMap = new HashMap<String, Integer>();
         
        studentMap.put("Jyous", 87);
        studentMap.put("Klusener", 82);
        studentMap.put("Xiangh", 91);
        studentMap.put("Lisa", 89);
        studentMap.put("Narayan", 95);
        studentMap.put("Arunkumar", 86);
                 
        Map<String, Integer> sortedStudentMap = new TreeMap<>(Collections.reverseOrder());
                 
        sortedStudentMap.putAll(studentMap);
         
        System.out.println("Before Sorting : ");
         
        System.out.println(studentMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedStudentMap);
    }
}
```
### SortMapByValuesProgram

```java
package CoreQuestion.sortMapJava8;

import java.util.Collections;
import java.util.Comparator;
import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.List;
import java.util.Map;
import java.util.Map.Entry;
 
public class SortMapByValuesProgram 
{
    public static void main(String[] args) 
    {
        //Define one HashMap called idNameMap
         
        Map<Integer, String> idNameMap = new HashMap<Integer, String>();
         
        //Insert Id-Name pairs into idNameMap
         
        idNameMap.put(111, "Lisa");
        idNameMap.put(222, "Narayan");
        idNameMap.put(333, "Xiangh");
        idNameMap.put(444, "Arunkumar");
        idNameMap.put(555, "Jyous");
        idNameMap.put(666, "Klusener");
         
        //Get listOfEntry through entrySet() method
         
        List<Entry<Integer, String>> listOfEntry = new LinkedList<>(idNameMap.entrySet());
         
        //Sort listOfEntry using Collections.sort() by passing customized Comparator
         
        Collections.sort(listOfEntry, new Comparator<Entry<Integer, String>>() 
        {
            @Override
            public int compare(Entry<Integer, String> o1, Entry<Integer, String> o2) 
            {
                return o1.getValue().compareTo(o2.getValue());
            }
        });
         
        //Insert all elements of listOfEntry into new LinkedHashMap which maintains insertion order
         
        Map<Integer, String> sortedIdNameMap = new LinkedHashMap<Integer, String>();
         
        for (Entry<Integer, String> entry : listOfEntry) 
        {
            sortedIdNameMap.put(entry.getKey(), entry.getValue());
        }
         
        //Print idNameMap before and after sorting
         
        System.out.println("Before Sorting : ");
         
        System.out.println(idNameMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedIdNameMap);
    }
}
```

### SortMapByValuesProgramFive

```java
package CoreQuestion.sortMapJava8;

import java.util.Collections;
import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByValuesProgramFive 
{
    public static void main(String[] args) 
    {
        //Define one HashMap called idNameMap
         
        Map<Integer, String> idNameMap = new HashMap<Integer, String>();
         
        //Insert Id-Name pairs into idNameMap
         
        idNameMap.put(111, "Lisa");
        idNameMap.put(222, "Narayan");
        idNameMap.put(333, "Xiangh");
        idNameMap.put(444, "Arunkumar");
        idNameMap.put(555, "Jyous");
        idNameMap.put(666, "Klusener");
         
        //Java 8 sorting using Entry.comparingByValue()
         
        Map<Integer, String> sortedIdNameMap 
        = idNameMap.entrySet()
                   .stream()
                   .sorted(Entry.comparingByValue((o1, o2) -> o2.length() - o1.length()))
                    
                   //OR
                   //.sorted(Collections.reverseOrder(Entry.comparingByValue((o1, o2) -> o1.length() - o2.length())))
                    
                   .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1,  e2) -> e1, LinkedHashMap::new));
 
        //Print idNameMap before and after sorting
         
        System.out.println("Before Sorting : ");
         
        System.out.println(idNameMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedIdNameMap);
    }
}
```

### SortMapByValuesProgramFour

```java
package CoreQuestion.sortMapJava8;

import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByValuesProgramFour 
{
    public static void main(String[] args) 
    {
        //Define one HashMap called idNameMap
         
        Map<Integer, String> idNameMap = new HashMap<Integer, String>();
         
        //Insert Id-Name pairs into idNameMap
         
        idNameMap.put(111, "Lisa");
        idNameMap.put(222, "Narayan");
        idNameMap.put(333, "Xiangh");
        idNameMap.put(444, "Arunkumar");
        idNameMap.put(555, "Jyous");
        idNameMap.put(666, "Klusener");
         
        //Java 8 sorting using Entry.comparingByValue()
         
        Map<Integer, String> sortedIdNameMap 
        = idNameMap.entrySet()
                   .stream()
                   .sorted(Entry.comparingByValue((o1, o2) -> o1.length() - o2.length()))
                   .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1,  e2) -> e1, LinkedHashMap::new));
 
        //Print idNameMap before and after sorting
         
        System.out.println("Before Sorting : ");
         
        System.out.println(idNameMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedIdNameMap);
    }
}
```

### SortMapByValuesProgramThree

```java
package CoreQuestion.sortMapJava8;

import java.util.Collections;
import java.util.Comparator;
import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByValuesProgramThree 
{
    public static void main(String[] args) 
    {
        //Define one HashMap called idNameMap
         
        Map<Integer, String> idNameMap = new HashMap<Integer, String>();
         
        //Insert Id-Name pairs into idNameMap
         
        idNameMap.put(111, "Lisa");
        idNameMap.put(222, "Narayan");
        idNameMap.put(333, "Xiangh");
        idNameMap.put(444, "Arunkumar");
        idNameMap.put(555, "Jyous");
        idNameMap.put(666, "Klusener");
         
        //Java 8 sorting using Entry.comparingByValue()
         
        Map<Integer, String> sortedIdNameMap 
        = idNameMap.entrySet()
                   .stream()
                   .sorted(Collections.reverseOrder(Entry.comparingByValue()))
                   
                 // OR  
                 // .sorted(Entry.comparingByValue(Comparator.reverseOrder()))
                    
                   .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1,  e2) -> e1, LinkedHashMap::new));
 
         
        //Print idNameMap before and after sorting
         
        System.out.println("Before Sorting : ");
         
        System.out.println(idNameMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedIdNameMap);
    }
}
```

### SortMapByValuesProgramTwo

```java
package CoreQuestion.sortMapJava8;

import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;
 
public class SortMapByValuesProgramTwo 
{
    public static void main(String[] args) 
    {
        //Define one HashMap called idNameMap
         
        Map<Integer, String> idNameMap = new HashMap<Integer, String>();
         
        //Insert Id-Name pairs into idNameMap
         
        idNameMap.put(111, "Lisa");
        idNameMap.put(222, "Narayan");
        idNameMap.put(333, "Xiangh");
        idNameMap.put(444, "Arunkumar");
        idNameMap.put(555, "Jyous");
        idNameMap.put(666, "Klusener");
         
        //Java 8 sorting using Entry.comparingByValue()
         
        Map<Integer, String> sortedIdNameMap 
        = idNameMap.entrySet()
                   .stream()
                   .sorted(Entry.comparingByValue())
                   .collect(Collectors.toMap(Entry::getKey, Entry::getValue, (e1,  e2) -> e1, LinkedHashMap::new));
 
         
        //Print idNameMap before and after sorting
         
        System.out.println("Before Sorting : ");
         
        System.out.println(idNameMap);
         
        System.out.println("After Sorting : ");
         
        System.out.println(sortedIdNameMap);
    }
}
```

## ArrayReverseExample

```java
package CoreQuestion;

import java.util.Arrays;
 
public class ArrayReverseExample 
{  
    static void reverseArray(int inputArray[])
    {
        System.out.println("Array Before Reverse : "+Arrays.toString(inputArray));
         
        int temp;
         
        for (int i = 0; i < inputArray.length/2; i++) 
        {
            temp = inputArray[i];
             
            inputArray[i] = inputArray[inputArray.length-1-i];
             
            inputArray[inputArray.length-1-i] = temp;
        }
         
        System.out.println("Array After Reverse : "+Arrays.toString(inputArray));
    }
     
    public static void main(String[] args) 
    {   
        reverseArray(new int[]{4, 5, 8, 9, 10});
         
        System.out.println("-------------------------");
         
        reverseArray(new int[]{12, 9, 21, 17, 33, 7});
         
        System.out.println("-------------------------");
         
        reverseArray(new int[]{891, 569, 921, 187, 343, 476, 555});
    }   
}
```

## CommonCharsOfTwoStrings

```java
package CoreQuestion;

import java.util.Scanner;
import java.util.Set;
import java.util.TreeSet;

public class CommonCharsOfTwoStrings
{
    private static void printCommonChars(String firstString, String secondString) {
        char[] firstStringToCharArray = firstString.replaceAll("\\s+", "").toCharArray();

        char[] secondStringToCharArray = secondString.replaceAll("\\s+", "").toCharArray();

        Set<Character> firstStringSet = new TreeSet<>();

        Set<Character> secondStringSet = new TreeSet<>();

        for (char c : firstStringToCharArray) {
            firstStringSet.add(c);
        }

        for (char c : secondStringToCharArray) {
            secondStringSet.add(c);
        }

        firstStringSet.retainAll(secondStringSet);

        System.out.println("Common characters in alphabetical order : "+firstStringSet);

        System.out.println("Count : "+firstStringSet.size());
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter two input strings :");

        String firstString = sc.nextLine();

        String secondString = sc.nextLine();

        printCommonChars(firstString, secondString);

        sc.close();
    }
}
```

## CommonElements

```java
package CoreQuestion;

import java.util.HashSet;
//Write a java program to find intersection of two arrays
class CommonElements
{
    public static void main(String[] args)
    {
        String[] s1 = {"ONE", "TWO", "THREE", "FOUR", "FIVE", "FOUR"};
 
        String[] s2 = {"THREE", "FOUR", "FIVE", "SIX", "SEVEN", "FOUR"};
 
        HashSet<String> set = new HashSet<String>();
 
        for (int i = 0; i < s1.length; i++)
        {
            for (int j = 0; j < s2.length; j++)
            {
                if(s1[i].equals(s2[j]))
                {
                    set.add(s1[i]);
                }
            }
        }
 
        System.out.println(set);     //OUTPUT : [THREE, FOUR, FIVE]
    }
}
```

## CommonElementsTwo

```java
package CoreQuestion;

import java.util.Arrays;
import java.util.HashSet;

class CommonElementsTwo
{
    public static void main(String[] args)
    {
        Integer[] i1 = {1, 2, 3, 4, 5, 4};
 
        Integer[] i2 = {3, 4, 5, 6, 7, 4};
 
        HashSet<Integer> set1 = new HashSet<>(Arrays.asList(i1));
 
        HashSet<Integer> set2 = new HashSet<>(Arrays.asList(i2));
 
        set1.retainAll(set2);
 
        System.out.println(set1);     //Output : [3, 4, 5]
    }
}
```

## ExampleFive

```java
package CoreQuestion;

import java.util.HashMap;
 
public class ExampleFive 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap
         
        HashMap<Integer, Double> map = new HashMap<Integer, Double>();
         
        //Adding key-value pairs to HashMap
         
        map.put(1, 1.1);
         
        map.put(2, 2.2);
         
        map.put(3, 3.3);
         
        map.put(4, 4.4);
         
        //Checking whether key '3' exist in map
         
        System.out.println(map.containsKey(3));      //Output : true
         
        //Checking whether value '3.3' exist in map
         
        System.out.println(map.containsValue(3.3));   //Output : true
    }   
}
```

## ExampleOne

```java
package CoreQuestion;

import java.util.HashMap;
  
public class ExampleOne 
{    
    public static void main(String[] args) 
    {
        //1. Creating HashMap with default initial capacity and load factor
         
        HashMap<String, Integer> map1 = new HashMap<String, Integer>();
         
        //2. Creating HashMap with 30 as initial capacity 
         
        HashMap<String, Integer> map2 = new HashMap<String, Integer>(30);
         
        //3. Creating HashMap with 30 as initial capacity and 0.5 as load factor
         
        HashMap<String, Integer> map3 = new HashMap<String, Integer>(30, 0.5f);
         
        //4. Creating HashMap by copying another HashMap
         
        HashMap<String, Integer> map4 = new HashMap<String, Integer>(map1);
    }   
}
```

## FibonacciSeries

```java
package CoreQuestion;

import java.util.Scanner;
 
public class FibonacciSeries 
{    
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
         
        System.out.println("Enter positive number :");
         
        int inputNumber = sc.nextInt();
         
        int firstTerm = 0;
         
        int secondTerm = 1;
         
        int thirdTerm = 0;
         
        while (thirdTerm < inputNumber)
        {
            thirdTerm = firstTerm + secondTerm;
             
            firstTerm = secondTerm;
             
            secondTerm = thirdTerm;
        }
         
        if(thirdTerm == inputNumber)
        {
            System.out.println("Number belongs to Fibonacci series");
        }
        else
        {
            System.out.println("Number doesn't belongs to Fibonacci series");
        }
    }   
}
```

## HashMapExampleFour
```java
package CoreQuestion;

import java.util.HashMap;
 
public class HashMapExampleFour 
{    
    public static void main(String[] args) 
    {
        //Creating HashMap with default initial capacity and load factor
         
        HashMap<String, Integer> map = new HashMap<String, Integer>();
         
        //Adding key-value pairs to HashMap
         
        map.put("ONE", 1);
         
        map.put("TWO", 2);
         
        map.put("THREE", 3);
         
        map.put("FOUR", 4);
         
        //Retrieving a value associated with key 'TWO'
         
        int value = map.get("TWO");
         
        System.out.println(value);       //Output : 2
    }   
}
```

## HashMapExampleNine

```java

package CoreQuestion;

import java.util.Collection;
import java.util.HashMap;
  
public class HashMapExampleNine 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<Integer, String> map = new HashMap<Integer, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put(1, "AAA");
         
        map.put(2, "BBB");
         
        map.put(3, "CCC");
         
        map.put(4, "DDD");
         
        map.put(5, "EEE");
         
        //Retrieving the Collection view of values present in map
         
        Collection<String> values = map.values();
         
        for (String value : values) 
        {
            System.out.println(value);
        }
    }   
}
```

## HashMapExampleThree

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class HashMapExampleThree 
{    
    public static void main(String[] args) 
    {
        //Creating HashMap with default initial capacity and load factor
         
        HashMap<String, Integer> map = new HashMap<String, Integer>();
         
        //Adding key-value pairs
         
        map.put("ONE", 1);
         
        map.put("TWO", 2);
         
        map.put("THREE", 3);
         
        map.put("FOUR", 4);
         
        //Adds key-value pair 'ONE-111' only if it is not present in map
         
        map.putIfAbsent("ONE", 111);
         
        //Adds key-value pair 'FIVE-5' only if it is not present in map
         
        map.putIfAbsent("FIVE", 5);
         
        //Printing key-value pairs of map
         
        Set<Entry<String, Integer>> entrySet = map.entrySet();
                 
        for (Entry<String, Integer> entry : entrySet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }       
    }   
}
```

## JavaHashMapExample

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Set;
  
public class JavaHashMapExample 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<Integer, String> map = new HashMap<Integer, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put(1, "AAA");
         
        map.put(2, "BBB");
         
        map.put(3, "CCC");
         
        map.put(4, "DDD");
         
        map.put(5, "EEE");
         
        //Retrieving the Key Set
         
        Set<Integer> keySet = map.keySet();
         
        for (Integer key : keySet) 
        {
            System.out.println(key);
        }
    }   
}
```

## JavaHashMapExampleEleven

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class JavaHashMapExampleEleven 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<String, String> map = new HashMap<String, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put("ONE", "AAA");
         
        map.put("TWO", "BBB");
         
        map.put("THREE", "CCC");
         
        map.put("FOUR", "DDD");
         
        map.put("FIVE", "EEE");
         
        //Printing Key-value pairs
         
        System.out.println("HashMap Before Remove :");
         
        Set<Entry<String, String>> keyValueSet = map.entrySet();
         
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
         
        System.out.println("------------------");
         
        //Removes the mapping for the key 'ONE' only if it is currently mapped to 'CCC'
         
        map.remove("ONE", "CCC");
         
        //Removes the mapping for the key 'FIVE' only if it is currently mapped to 'EEE'
         
        map.remove("FIVE", "EEE");
         
        System.out.println("HashMap After Remove :");
         
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }   
}
```
## JavaHashMapExampleFourtyinth

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class JavaHashMapExampleFourtyinth 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<String, String> map = new HashMap<String, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put("ONE", "AAA");
         
        map.put("TWO", "BBB");
         
        map.put("THREE", "CCC");
         
        map.put("FOUR", "DDD");
         
        map.put("FIVE", "EEE");
         
        //Printing Key-value pairs
         
        System.out.println("HashMap Before Replace :");
                 
        Set<Entry<String, String>> keyValueSet = map.entrySet();
                 
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
                 
        System.out.println("------------------");
         
        //Replacing the value associated with 'FOUR' to '444' only if it is currently mapped to 'DDD'
         
        map.replace("FOUR", "DDD", "444");
         
        System.out.println("HashMap After Replace :");
                 
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }   
}
```

## JavaHashMapExampleSeven

```java
package CoreQuestion;

import java.util.HashMap;
 
public class JavaHashMapExampleSeven 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap
         
        HashMap<Integer, Double> map = new HashMap<Integer, Double>();
         
        //Adding key-value pairs to HashMap
         
        map.put(111, 111.111);
         
        map.put(222, 222.222);
         
        map.put(333, 333.333);
         
        map.put(444, 444.444);
         
        map.put(555, 555.555);
         
        //Retrieving the number of key-value pairs
         
        System.out.println(map.size());      //Output : 5
         
        //Clearing the map
         
        map.clear();
         
        //Checking the number of key-value pairs after clearing the map
         
        System.out.println(map.size());      //Output : 0
    }   
}
```

## JavaHashMapPrograms

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class JavaHashMapPrograms 
{    
    public static void main(String[] args) 
    {
        //Creating HashMap with default initial capacity and load factor
         
        HashMap<String, Integer> map = new HashMap<String, Integer>();
         
        //Inserting key-value pairs to map using put() method
         
        map.put("ONE", 1);
         
        map.put("TWO", 2);
         
        map.put("THREE", 3);
         
        map.put("FOUR", 4);
         
        map.put("FIVE", 5);
         
        //Printing key-value pairs 
         
        Set<Entry<String, Integer>> entrySet = map.entrySet();
         
        for (Entry<String, Integer> entry : entrySet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
         
        System.out.println("-------------------------");
         
        //Creating another HashMap
         
        HashMap<String, Integer> anotherMap = new HashMap<String, Integer>();
         
        //Inserting key-value pairs to anotherMap using put() method
         
        anotherMap.put("SIX", 6);
         
        anotherMap.put("SEVEN", 7);
         
        //Inserting key-value pairs of map to anotherMap using putAll() method
         
        anotherMap.putAll(map);
         
        //Printing key-value pairs of anotherMap
         
        entrySet = anotherMap.entrySet();
         
        for (Entry<String, Integer> entry : entrySet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }   
}
```

## JavaHashMapProgramsSix

```java
package CoreQuestion;

import java.util.HashMap;
 
public class JavaHashMapProgramsSix 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<Integer, Double> map = new HashMap<Integer, Double>();
         
        //Adding key-value pairs to HashMap
         
        map.put(111, 111.111);
         
        map.put(222, 222.222);
         
        map.put(333, 333.333);
         
        map.put(444, 444.444);
         
        map.put(555, 555.555);
         
        //Retrieving the number of key-value pairs present in map
         
        System.out.println(map.size());      //Output : 5
    }   
}
```

## JavaHashMapProgramsTen

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
  
public class JavaHashMapProgramsTen 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<String, String> map = new HashMap<String, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put("ONE", "AAA");
         
        map.put("TWO", "BBB");
         
        map.put("THREE", "CCC");
         
        map.put("FOUR", "DDD");
         
        map.put("FIVE", "EEE");
         
        //Retrieving the Set consists of all key-value pairs in map
         
        Set<Entry<String, String>> keyValueSet = map.entrySet();
         
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }   
}

```

## JavaHashMapProgramsTwelve

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class JavaHashMapProgramsTwelve 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<String, String> map = new HashMap<String, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put("ONE", "AAA");
         
        map.put("TWO", "BBB");
         
        map.put("THREE", "CCC");
         
        map.put("FOUR", "DDD");
         
        map.put("FIVE", "EEE");
         
        //Printing Key-value pairs
         
        System.out.println("HashMap Before Replace :");
                 
        Set<Entry<String, String>> keyValueSet = map.entrySet();
                 
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
                 
        System.out.println("------------------");
         
        //Replacing the value associated with 'THREE' to '333'
         
        map.replace("THREE", "333");
         
        System.out.println("HashMap After Replace :");
                 
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }   
}
```

## LongestSubStringWithoutRepeating

```java

package CoreQuestion;

import java.util.LinkedHashMap;
import java.util.stream.Collectors;

public class LongestSubStringWithoutRepeating 
{  
    static void longestSubstring(String inputString)
    {
        //Convert inputString to charArray
         
        char[] charArray = inputString.toCharArray();
         
        //Initialization
         
        String longestSubstring = null;
         
        int longestSubstringLength = 0;
         
        //Creating LinkedHashMap with characters as keys and their position as values.
         
        LinkedHashMap<Character, Integer> charPosMap = new LinkedHashMap<Character, Integer>();
         
        //Iterating through charArray
         
        for (int i = 0; i < charArray.length; i++) 
        {
            char ch = charArray[i];
         
            //If ch is not present in charPosMap, adding ch into charPosMap along with its position
             
            if(!charPosMap.containsKey(ch))
            {
                charPosMap.put(ch, i);
            }
             
            //If ch is already present in charPosMap, reposioning the cursor i to the position of ch and clearing the charPosMap
             
            else
            {   
                i = charPosMap.get(ch);
                 
                charPosMap.clear();
            }
             
            //Updating longestSubstring and longestSubstringLength
             
            if(charPosMap.size() > longestSubstringLength)
            {
                longestSubstringLength = charPosMap.size();
                 
                //longestSubstring = charPosMap.keySet().toString();

                longestSubstring = charPosMap.keySet().stream().map(String::valueOf).collect(Collectors.joining());
            }
        }
         
        System.out.println("Input String : "+inputString);

        System.out.println("The longest substring : "+longestSubstring);
         
        System.out.println("The longest Substring Length : "+longestSubstringLength);
    }
     
    public static void main(String[] args) 
    {   
        longestSubstring("javaconceptoftheday");
         
        System.out.println("==========================");
         
        longestSubstring("thelongestsubstring");

        System.out.println("==========================");

        longestSubstring("Iamjavadeveloper");

    }   
}
```

## MainClass

```java
package CoreQuestion;

import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class MainClass 
{    
    public static void main(String[] args) 
    {
        //Creating the HashMap 
         
        HashMap<String, String> map = new HashMap<String, String>();
         
        //Adding key-value pairs to HashMap
         
        map.put("ONE", "AAA");
         
        map.put("TWO", "BBB");
         
        map.put("THREE", "CCC");
         
        map.put("FOUR", "DDD");
         
        map.put("FIVE", "EEE");
         
        //Printing key-value pairs
         
        System.out.println("HashMap Before Remove :");
         
        Set<Entry<String, String>> keyValueSet = map.entrySet();
         
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
         
        System.out.println("---------------------");
         
        //Removing the mapping for the key 'ONE'
         
        map.remove("ONE");
         
        System.out.println("HashMap After Remove :");
         
        for (Entry<String, String> entry : keyValueSet) 
        {
            System.out.println(entry.getKey()+" : "+entry.getValue());
        }
    }   
}
```

## MainClassLongeshSubStringWithoutRepeatingCharacter

```java
package CoreQuestion;

import java.util.LinkedHashMap;
 
public class MainClassLongeshSubStringWithoutRepeatingCharacter 
{  
    static void longestSubstring(String inputString)
    {
        //Convert inputString to charArray
         
        char[] charArray = inputString.toCharArray();
         
        //Initialization
         
        String longestSubstring = null;
         
        int longestSubstringLength = 0;
         
        //Creating LinkedHashMap with characters as keys and their position as values.
         
        LinkedHashMap<Character, Integer> charPosMap = new LinkedHashMap<Character, Integer>();
         
        //Iterating through charArray
         
        for (int i = 0; i < charArray.length; i++) 
        {
            char ch = charArray[i];
         
            //If ch is not present in charPosMap, adding ch into charPosMap along with its position
             
            if(!charPosMap.containsKey(ch))
            {
                charPosMap.put(ch, i);
            }
             
            //If ch is already present in charPosMap, reposioning the cursor i to the position of ch and clearing the charPosMap
             
            else
            {   
                i = charPosMap.get(ch);
                 
                charPosMap.clear();
            }
             
            //Updating longestSubstring and longestSubstringLength
             
            if(charPosMap.size() > longestSubstringLength)
            {
                longestSubstringLength = charPosMap.size();
                 
                longestSubstring = charPosMap.keySet().toString();
            }
        }
         
        System.out.println("Input String : "+inputString);
         
        System.out.println("The longest substring : "+longestSubstring);
         
        System.out.println("The longest Substring Length : "+longestSubstringLength);
    }
     
    public static void main(String[] args) 
    {   
        longestSubstring("javaconceptoftheday");
         
        System.out.println("==========================");
         
        longestSubstring("thelongestsubstring");
    }   
}
```

## MainClassPercentageOfAlphaNumeric

```java
package CoreQuestion;

import java.text.DecimalFormat;
 
public class MainClassPercentageOfAlphaNumeric
{   
    static void characterPercentage(String inputString)
    {
        //Getting total no of characters in the given string
         
        int totalChars = inputString.length();
         
        //Initializing upperCaseLetters, lowerCaseLetters, digits and others with 0
         
        int upperCaseLetters = 0;
         
        int lowerCaseLetters = 0;
         
        int digits = 0;
         
        int others = 0;
         
        //Iterating through each character of inputString
         
        for (int i = 0; i < inputString.length(); i++) 
        {
            char ch = inputString.charAt(i);
             
            //If ch is in uppercase, then incrementing upperCaseLetters
             
            if(Character.isUpperCase(ch))
            {
                upperCaseLetters++;
            }
             
            //If ch is in lowercase, then incrementing lowerCaseLetters
             
            else if(Character.isLowerCase(ch))
            {
                lowerCaseLetters++;
            }
             
            //If ch is a digit, then incrementing digits
             
            else if (Character.isDigit(ch))
            {
                digits++;
            }
             
            //If ch is a special character then incrementing others
             
            else
            {
                others++;
            }
        }
         
        //Calculating percentage of uppercase letters, lowercase letters, digits and other characters
         
        double upperCaseLetterPercentage = (upperCaseLetters * 100.0) / totalChars ;
         
        double lowerCaseLetterPercentage = (lowerCaseLetters * 100.0) / totalChars;
         
        double digitsPercentage = (digits * 100.0) / totalChars;
         
        double otherCharPercentage = (others * 100.0) / totalChars;
         
        DecimalFormat formatter = new DecimalFormat("##.##");
         
        //Printing percentage of uppercase letters, lowercase letters, digits and other characters
         
        System.out.println("In '"+inputString+"' : ");
         
        System.out.println("Uppercase letters are "+formatter.format(upperCaseLetterPercentage)+"% ");
         
        System.out.println("Lowercase letters are "+formatter.format(lowerCaseLetterPercentage)+"%");
         
        System.out.println("Digits Are "+formatter.format(digitsPercentage)+"%");
         
        System.out.println("Other Characters Are "+formatter.format(otherCharPercentage)+"%");
         
        System.out.println("-----------------------------");
    }
     
    public static void main(String[] args) 
    {
        characterPercentage("Tiger Runs @ The Speed Of 100 km/hour.");
         
        characterPercentage("My e-mail : eMail_Address321@anymail.com");
         
        characterPercentage("AUS : 123/3, 21.2 Overs");
    }
}
```

## MainClassRandomFour

```java
package CoreQuestion;

import java.util.Random;
import java.util.concurrent.ThreadLocalRandom;

public class MainClassRandomFour
{
    public static void main(String[] args)
    {
        //Generating random integers between 0 and 50 using Random class
 
        System.out.println("Random integers between 0 and 50 using Random class :");
 
        Random random = new Random();
 
        for (int i = 0; i < 5; i++)
        {
            System.out.println(random.nextInt(50));
        }
 
        //Generating random integers between 0 and 50 range using Math.random()
 
        System.out.println("Random integers between 0 and 50 using Math.random() :");
 
        for (int i = 0; i < 5; i++)
        {
            System.out.println((int)(Math.random() * 50));
        }
 
        //Generating random integers between 0 and 50 using ThreadLoclaRandom
 
        System.out.println("Random integers between 0 and 50 using ThreadLocalRandom :");
 
        for (int i = 0; i < 5; i++)
        {
            System.out.println(ThreadLocalRandom.current().nextInt(0, 50));
        }
    }
}
```

## MainClassRandomOne

```java
package CoreQuestion;

import java.util.Random;

public class MainClassRandomOne
{
    public static void main(String[] args)
    {
        Random random = new Random();

        //Generating random integers using Random class

        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random Integers : "+random.nextInt());
        }

        System.out.println("-----------------------------");

        //Generating random doubles using Random class

        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random Doubles : "+random.nextDouble());
        }

        System.out.println("-----------------------------");

        //Generating random booleans using Random class

        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random booleans : "+random.nextBoolean());
        }
    }
}
```

## MainClassRandomThree

```java
package CoreQuestion;

import java.util.concurrent.ThreadLocalRandom;

public class MainClassRandomThree
{
    public static void main(String[] args)
    {
        //Generating random integers using ThreadLocalRandom class
 
        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random Integers : "+ ThreadLocalRandom.current().nextInt());
        }
 
        System.out.println("-----------------------------");
 
        //Generating random doubles using ThreadLocalRandom class
 
        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random Doubles : "+ThreadLocalRandom.current().nextDouble());
        }
 
        System.out.println("-----------------------------");
 
        //Generating random booleans using ThreadLocalRandom class
 
        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random booleans : "+ThreadLocalRandom.current().nextBoolean());
        }
    }
}
```

## MainClassRandomTwo

```java
package CoreQuestion;

public class MainClassRandomTwo
{
    public static void main(String[] args)
    {
        //Generating random doubles using Math.random()
 
        for(int i = 0; i < 5; i++)
        {
            System.out.println("Random Doubles : "+Math.random());
        }
    }
}
```

## MainClassRemoveVowels

```java
package CoreQuestion;

import java.util.Scanner;
 
public class MainClassRemoveVowels
{   
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
         
        System.out.println("Enter the string...");
         
        String inputString = sc.nextLine();
         
        String newInputString = inputString.replaceAll("[AEIOUaeiou]", "");
         
        System.out.println("The string without vowels...");
         
        System.out.println(newInputString);
         
        sc.close();
    }
}
```

## MainClassRepeatingOrNonRepeating

```java

package CoreQuestion;

import java.util.HashMap;
import java.util.Scanner;
 
public class MainClassRepeatingOrNonRepeating 
{
    static void firstRepeatedNonRepeatedChar(String inputString) {
        //Creating a HashMap containing char as a key and occurrences as a value

        HashMap<Character, Integer> charCountMap = new HashMap<Character, Integer>();

        //Converting inputString to char array

        char[] strArray = inputString.toCharArray();

        //Checking each char of strArray

        for (char c : strArray) {
            if(charCountMap.containsKey(c)) {
                //If char is present in charCountMap, incrementing it's count by 1

                charCountMap.put(c, charCountMap.get(c)+1);
            } else {
                //If char is not present in charCountMap,
                //adding this char in charCountMap with 1 as it's value

                charCountMap.put(c, 1);
            }
        }

        //checking for first non-repeated character

        for (char c : strArray) {
            if (charCountMap.get(c) == 1) {
                System.out.println("First Non-Repeated Character In '"+inputString+"' is '"+c+"'");

                break;
            }
        }

        //checking for first repeated character

        for (char c : strArray) {
            if (charCountMap.get(c) > 1) {
                System.out.println("First Repeated Character In '"+inputString+"' is '"+c+"'");

                break;
            }
        }
    }

    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter the string :");

        String input = sc.next();

        firstRepeatedNonRepeatedChar(input);
    }
}
```
## MainClassReverseStringTwoPreservingSpace

```java

package CoreQuestion;

public class MainClassReverseStringTwoPreservingSpace
{   
    static void reverseString(String inputString)
    {
        //Converting inputString to char array 'inputStringArray'
         
        char[] inputStringArray = inputString.toCharArray();
         
        //Defining a new char array 'resultArray' with same size as inputStringArray
         
        char[] resultArray = new char[inputStringArray.length];
         
        //First for loop : 
        //For every space in the 'inputStringArray', 
        //we insert spaces in the 'resultArray' at the corresponding positions 
         
        for (int i = 0; i < inputStringArray.length; i++) 
        {
            if (inputStringArray[i] == ' ') 
            {
                resultArray[i] = ' ';
            }
        }
         
        //Initializing 'j' with length of resultArray
         
        int j = resultArray.length-1;
                 
        //Second for loop :
        //we copy every non-space character of inputStringArray 
        //from first to last at 'j' position of resultArray
         
        for (int i = 0; i < inputStringArray.length; i++)
        {
            if (inputStringArray[i] != ' ') 
            {
                //If resultArray already has space at index j then decrementing 'j'
                 
                if(resultArray[j] == ' ')
                {
                    j--;
                }
                 
                resultArray[j] = inputStringArray[i];
                 
                j--;
            }
        }
         
        System.out.println(inputString+" ---> "+String.valueOf(resultArray));
    }
     
    public static void main(String[] args)
    {
        reverseString("I Am Not String");
         
        reverseString("JAVA JSP ANDROID");
         
        reverseString("1 22 333 4444 55555");
    }
}
```

## MostFrequentElementProgram

```java
package CoreQuestion;

import java.util.Arrays;
import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Set;
 
public class MostFrequentElementProgram
{   
    static void getMostFrequentElement(int inputArray[])
    {
        //Creating HashMap object with elements as keys and their occurrences as values
         
        HashMap<Integer, Integer> elementCountMap = new HashMap<Integer, Integer>();
         
        //Inserting all the elements of inputArray into elementCountMap
         
        for (int i : inputArray) 
        {
            if (elementCountMap.containsKey(i))
            {
                //If an element is present, incrementing its count by 1
                 
                elementCountMap.put(i, elementCountMap.get(i)+1);
            }
            else
            {
                //If an element is not present, put that element with 1 as its value
                 
                elementCountMap.put(i, 1);
            }
        }
         
        int element = 0;
         
        int frequency = 1;
         
        //Iterating through elementCountMap to get the most frequent element and its frequency
         
        Set<Entry<Integer, Integer>> entrySet = elementCountMap.entrySet();
         
        for (Entry<Integer, Integer> entry : entrySet) 
        {
            if(entry.getValue() > frequency)
            {
                element = entry.getKey();
                 
                frequency = entry.getValue();
            }
        }
         
        //Printing the most frequent element in array and its frequency
         
        if(frequency > 1)
        {
            System.out.println("Input Array : "+Arrays.toString(inputArray));
             
            System.out.println("The most frequent element : "+element);
             
            System.out.println("Its frequency : "+frequency);
             
            System.out.println("========================");
        }
        else
        {
            System.out.println("Input Array : "+Arrays.toString(inputArray));
             
            System.out.println("No frequent element. All elements are unique.");
             
            System.out.println("=========================");
        }
    }
     
    public static void main(String[] args)
    {
        getMostFrequentElement(new int[]{4, 5, 8, 7, 4, 7, 6,7});
         
        getMostFrequentElement(new int[]{1, 2, 7, 5, 3, 6});
    }
}
```

## PairsOfElementsInArray

```java
package CoreQuestion;

//Java Program To Find All Pairs Of Elements In An Array Whose Sum Is Equal To A Given Number
public class PairsOfElementsInArray {
    static void findThePairs(int inputArray[], int inputNumber) {
        System.out.println("Pairs of elements whose sum is " + inputNumber + " are : ");

        for (int i = 0; i < inputArray.length; i++) {
            for (int j = i + 1; j < inputArray.length; j++) {
                if (inputArray[i] + inputArray[j] == inputNumber) {
                    System.out.println(inputArray[i] + " + " + inputArray[j] + " = " + inputNumber);
                }
            }
        }
    }

    public static void main(String[] args) {
        findThePairs(new int[]{4, 6, 5, -10, 8, 5, 20}, 10);

        findThePairs(new int[]{4, -5, 9, 11, 25, 13, 12, 8}, 20);

        findThePairs(new int[]{12, 13, 40, 15, 8, 10, -15}, 25);

        findThePairs(new int[]{12, 23, 125, 41, -75, 38, 27, 11}, 50);
    }
}
```

## PairsOfElementsInArrayTwo

```java
package CoreQuestion;

import java.util.Arrays;

public class PairsOfElementsInArrayTwo
{
    static void findThePairs(int inputArray[], int inputNumber)
    {
        //Sorting the given array
 
        Arrays.sort(inputArray);
 
        System.out.println("Pairs of elements whose sum is "+inputNumber+" are : ");
 
        //Initializing i to first index
 
        int i = 0;
 
        //Initializing j to last index
 
        int j = inputArray.length-1;
 
        //Till i crosses j, perform the following task
 
        while (i < j)
        {
            //If inputArray[i]+inputArray[j] is equal to inputNumber
 
            if(inputArray[i]+inputArray[j] == inputNumber)
            {
                //then Print inputArray[i] and inputArray[j]
 
                System.out.println(inputArray[i]+" + "+inputArray[j]+" = "+inputNumber);
 
                //Increment i
 
                i++;
 
                //Decrement j
 
                j--;
            }
 
            //If inputArray[i]+inputArray[j] is smaller than inputNumber
 
            else if (inputArray[i]+inputArray[j] < inputNumber)
            {
                //then increment i
 
                i++;
            }
 
            //If inputArray[i]+inputArray[j] is greater than inputNumber
 
            else if (inputArray[i]+inputArray[j] > inputNumber)
            {
                //then decrement j
 
                j--;
            }
        }
    }
 
    public static void main(String[] args)
    {
        findThePairs(new int[] {4, 6, 5, -10, 8, 5, 20}, 10);
 
        findThePairs(new int[] {4, -5, 9, 11, 25, 13, 12, 8}, 20);
 
        findThePairs(new int[] {12, 13, 10, 15, 8, 40, -15}, 25);
 
        findThePairs(new int[] {12, 23, 10, 41, 15, 38, 27}, 50);
    }
}

```

## PalindromeProgram

```java
package CoreQuestion;

import java.util.Scanner;
 
public class PalindromeProgram
{
    private static boolean isItPalindrome(String inputString)
    {
        //Clean inpuString by removing spaces and negating the case of the letters
         
        String cleanInputString = inputString.replaceAll("\\s+", "").toLowerCase();
         
        //Convert cleanInputString to char array
         
        char[] charArray = cleanInputString.toCharArray();
         
        //Let forward index point at first character
         
        int forward = 0;
         
        //And backward index point at last character
         
        int backward = charArray.length - 1;
         
        //start iterating charArray from both ends simultaneously
         
        while (forward <= backward)
        {
            if(charArray[forward] != charArray[backward])
            {
                //If chars at both ends are not same, return false
                 
                return false;
            }
             
            //If chars at both ends are same, increment forward and decrement backward
             
            forward++;
             
            backward--;
        }
         
        return true;
    }
     
    public static void main(String[] args)
    {
        //Take the input string from the user
         
        System.out.println("Enter the input String...");
         
        Scanner sc = new Scanner(System.in);
         
        String inputString = sc.nextLine();
         
        if (isItPalindrome(inputString)) 
        {
            System.out.println(inputString+" is a palindrome");
        }
        else
        {
            System.out.println(inputString+" is not a palindrome");
        }
         
        sc.close();
    }
}
```

## PermutationsOfString

```java
package CoreQuestion;

public class PermutationsOfString
{   
    static public void StringPermutation(String input)
    {
        StringPermutation("", input);
    }
     
    private static void StringPermutation(String permutation, String input)
    {   
        if(input.length() == 0)
        {
            System.out.println(permutation);
        }
        else
        {
            for (int i = 0; i < input.length(); i++)
            {   
                StringPermutation(permutation+input.charAt(i), input.substring(0, i)+input.substring(i+1, input.length()));
            }
        }
    }
     
    public static void main(String[] args) 
    {
        StringPermutation("JSP");
    }   
}
```

## RemoveDuplicatesJavaExample

```java
package CoreQuestion;

import java.util.Arrays;
 
public class RemoveDuplicatesJavaExample 
{   
    static void removeDuplicates(int[] arrayWithDuplicates)
    {
        System.out.println("Array With Duplicates : ");
         
        for (int i = 0; i < arrayWithDuplicates.length; i++)
        {
            System.out.print(arrayWithDuplicates[i]+"\t");
        }
         
        //Assuming all elements in input array are unique
         
        int noOfUniqueElements = arrayWithDuplicates.length;
         
        //Comparing each element with all other elements
         
        for (int i = 0; i < noOfUniqueElements; i++) 
        {
            for (int j = i+1; j < noOfUniqueElements; j++)
            {
                //If any two elements are found equal
                 
                if(arrayWithDuplicates[i] == arrayWithDuplicates[j])
                {
                    //Replace duplicate element with last unique element
                     
                    arrayWithDuplicates[j] = arrayWithDuplicates[noOfUniqueElements-1];
                     
                    //Decrementing noOfUniqueElements
                     
                    noOfUniqueElements--;
                     
                    //Decrementing j
                     
                    j--;
                }
            }
        }
         
        //Copying only unique elements of arrayWithDuplicates into arrayWithoutDuplicates
         
        int[] arrayWithoutDuplicates = Arrays.copyOf(arrayWithDuplicates, noOfUniqueElements);
         
        //Printing arrayWithoutDuplicates
         
        System.out.println();
         
        System.out.println("Array Without Duplicates : ");
         
        for (int i = 0; i < arrayWithoutDuplicates.length; i++)
        {
            System.out.print(arrayWithoutDuplicates[i]+"\t");
        }
         
        System.out.println();
         
        System.out.println("==============================");
    }
     
    public static void main(String[] args) 
    {       
        removeDuplicates(new int[] {4, 3, 2, 4, 9, 2});
         
        removeDuplicates(new int[] {1, 2, 1, 2, 1, 2});
         
        removeDuplicates(new int[] {15, 21, 11, 21, 51, 21, 11});
         
        removeDuplicates(new int[] {7, 3, 21, 7, 34, 18, 3, 21});
    }   
}
```

## RemoveDuplicatesJavaExampleTwo

```java
package CoreQuestion;

import java.util.LinkedHashSet;
import java.util.Set;
 
public class RemoveDuplicatesJavaExampleTwo 
{   
    static void removeDuplicates(int[] arrayWithDuplicates)
    {
        System.out.println("Array With Duplicates : ");
         
        for (int i = 0; i < arrayWithDuplicates.length; i++)
        {
            System.out.print(arrayWithDuplicates[i]+"\t");
        }
         
        Set<Integer> set = new LinkedHashSet<Integer>();      //Use HashSet if you don't want insertion order
         
        for (int i = 0; i < arrayWithDuplicates.length; i++) 
        {
            set.add(arrayWithDuplicates[i]);
        }
         
        //Converting set into an array
         
        Object[] arrayWithoutDuplicates = set.toArray();
 
        //Printing arrayWithoutDuplicates
                 
        System.out.println();
                 
        System.out.println("Array Without Duplicates : ");
                 
        for (int i = 0; i < arrayWithoutDuplicates.length; i++)
        {
            System.out.print(arrayWithoutDuplicates[i]+"\t");
        }
                 
        System.out.println();
                 
        System.out.println("==============================");
    }
     
    public static void main(String[] args) 
    {       
        removeDuplicates(new int[] {4, 3, 2, 4, 9, 2});
         
        removeDuplicates(new int[] {1, 2, 1, 2, 1, 2});
         
        removeDuplicates(new int[] {15, 21, 11, 21, 51, 21, 11});
         
        removeDuplicates(new int[] {7, 3, 21, 7, 34, 18, 3, 21});
    }   
}
```

## RemoveWhiteSpaces

```java
package CoreQuestion;

import java.util.Scanner;

public class RemoveWhiteSpaces 
{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter input string to be cleaned from white spaces...!");

        String inputString = sc.nextLine();

        String stringWithoutSpaces = inputString.replaceAll("\\s+", "");

        System.out.println("Input String : "+inputString);

        System.out.println("Input String Without Spaces : "+stringWithoutSpaces);

        sc.close();
    }
}
```

## RemoveWhiteSpacesTwo

```java
package CoreQuestion;

import java.util.Scanner;

public class RemoveWhiteSpacesTwo
{
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
         
        System.out.println("Enter input string to be cleaned from white spaces...!");
         
        String inputString = sc.nextLine();
         
        char[] charArray = inputString.toCharArray();
         
        String stringWithoutSpaces = "";
         
        for (int i = 0; i < charArray.length; i++) 
        {
            if ( (charArray[i] != ' ') && (charArray[i] != '\t') )
            {
                stringWithoutSpaces = stringWithoutSpaces + charArray[i];
            }
        }
         
        System.out.println("Input String : "+inputString);
         
        System.out.println("Input String Without Spaces : "+stringWithoutSpaces);
         
        sc.close();
    }
}
```

## ReverseAddPalindrome

```java
package CoreQuestion;

import java.util.Scanner;
 
public class ReverseAddPalindrome
{
    //Method To Reverse A Number
     
    static int reverseNumber(int number)
    {
        int reverse = 0;
         
        int rem = 0;
         
        while (number != 0)
        {
            rem = number % 10;
             
            reverse = (reverse*10) + rem;
             
            number = number/10;
        }
         
        return reverse;
    }
     
    //Method To Check For Palindrome
     
    static boolean checkPalindrome(int number)
    {
        int reverse = reverseNumber(number);
         
        if(reverse == number)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
     
    //Method To Reverse And Add Given Number Until You Get A Palindrome
     
    static void reverseAndAdd(int number)
    {
        if(checkPalindrome(number))
        {
            System.out.println("Given Number is already a palindrome");
        }
        else
        {
            while (!checkPalindrome(number))
            {
                int reverse = reverseNumber(number);
                 
                int sum = number + reverse;
                 
                System.out.println(number+" + "+reverse+" = "+sum);
                 
                number = sum;
            }
        }
    }
     
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
         
        System.out.println("Enter Number : ");
         
        int inputNumber = sc.nextInt();
         
        reverseAndAdd(inputNumber);
    }
}
```

## ReverseEachWord

```java
package CoreQuestion;

public class ReverseEachWord
{
    static void reverseEachWordOfString(String inputString) {
        String[] words = inputString.split(" ");

        String reverseString = "";

        for (int i = 0; i < words.length; i++) {
            String word = words[i];

            String reverseWord = "";

            for (int j = word.length()-1; j >= 0; j--) {
                reverseWord = reverseWord + word.charAt(j);
            }

            reverseString = reverseString + reverseWord + " ";
        }

        System.out.println(inputString);

        System.out.println(reverseString);

        System.out.println("-------------------------");
    }

    public static void main(String[] args) 
    {
        reverseEachWordOfString("Java Concept Of The Day");

        reverseEachWordOfString("Java J2EE JSP Servlets Hibernate Struts");

        reverseEachWordOfString("I am string not reversed");

        reverseEachWordOfString("Reverse Me");
    }
}
```

## ReverseStringWordByWordProgram

```java
package CoreQuestion;

import java.util.Scanner;

public class ReverseStringWordByWordProgram 
{
    public static String reverseTheSentence(String inputString) {
        String[] words = inputString.split("\\s");

        String outputString = "";

        for (int i = words.length-1; i >= 0; i--) {
            outputString = outputString + words[i] + " ";
        }

        return outputString;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter Input String :");

        String inputString = sc.nextLine();

        String outputString = reverseTheSentence(inputString);

        System.out.println("Input String : "+inputString);

        System.out.println("Output String : "+outputString);

        sc.close();
    }
}
```

## SubArrayWhoseSumIsNumber

```java
package CoreQuestion;

import java.util.Arrays;
 
public class SubArrayWhoseSumIsNumber
{
    static void findSubArray(int[] inputArray, int inputNumber)
    {
        //Initializing sum with the first element of the inputArray
 
        int sum = inputArray[0];
 
        //Initializing starting point with 0
 
        int start = 0;
 
        //Iterating through inputArray starting from second element
 
        for (int i = 1; i < inputArray.length; i++)
        {
            //Adding inputArray[i] to the current 'sum'
 
            sum = sum + inputArray[i];
 
            //If sum is greater than inputNumber then following loop is executed until
 
            //sum becomes either smaller than or equal to inputNumber
 
            while(sum > inputNumber && start <= i-1)
            {
                //Removing starting elements from the 'sum'
 
                sum = sum - inputArray[start];
 
                //Incrementing start by 1
 
                start++;
            }
 
            //If 'sum' is equal to 'inputNumber' then printing the sub array
 
            if(sum == inputNumber)
            {
                System.out.println("Continuous sub array of "+Arrays.toString(inputArray)+" whose sum is "+inputNumber+" is ");
 
                for (int j = start; j <= i; j++)
                {
                    System.out.print(inputArray[j]+" ");
                }
 
                System.out.println();
            }
        }
    }
 
    public static void main(String[] args)
    {
        findSubArray(new int[]{42, 15, 12, 8, 6, 32}, 26);
 
        findSubArray(new int[]{12, 5, 31, 13, 21, 8}, 49);
 
        findSubArray(new int[]{15, 51, 7, 81, 5, 11, 25}, 41);
    }
}
```

## SubArrayWhoseSumIsNumberTwo

```java
package CoreQuestion;

import java.util.Arrays;
 
public class SubArrayWhoseSumIsNumberTwo
{
    static void findSubArray(int[] inputArray, int inputNumber)
    {
        //Initializing 'sum' to 0
 
        int sum = 0;
 
        //Iterating through 'inputArray'
 
        for (int i = 0; i < inputArray.length; i++)
        {
            //Assigning inputArray[i] to 'sum'
 
            sum = inputArray[i];
 
            for (int j = i+1; j < inputArray.length; j++)
            {
                //Adding inputArray[j] to 'sum'
 
                sum = sum + inputArray[j];
 
                //If 'sum' is equal to 'inputNumber' then printing the sub array
 
                if(sum == inputNumber)
                {
                    System.out.println("Continuous sub array of "+Arrays.toString(inputArray)+" whose sum is "+inputNumber+" is ");
 
                    for (int k = i; k <= j; k++)
                    {
                        System.out.print(inputArray[k]+" ");
                    }
 
                    System.out.println();
                }
 
                //if 'sum' is smaller than 'inputNumber', continue the loop
 
                else if (sum < inputNumber)
                {
                    continue;
                }
 
                //if 'sum' is greater than 'inputNumber', then break the loop
 
                else if (sum > inputNumber)
                {
                    break;
                }
            }
        }
    }
 
    public static void main(String[] args)
    {
        findSubArray(new int[]{42, 15, 12, 8, 6, 32}, 26);
 
        findSubArray(new int[]{12, 5, 31, 13, 21, 8}, 49);
 
        findSubArray(new int[]{15, 51, 7, 81, 5, 11, 25}, 41);
    }
}
```

## SwapTwoStrings

```java
package CoreQuestion;

import java.util.Scanner;
 
public class SwapTwoStrings 
{  
    public static void main(String[] args) 
    {   
        Scanner sc = new Scanner(System.in);
         
        System.out.println("Enter First String :");
         
        String s1 = sc.next();
         
        System.out.println("Enter Second String :");
         
        String s2 = sc.next();
         
        System.out.println("Before Swapping :");
         
        System.out.println("s1 : "+s1);
         
        System.out.println("s2 : "+s2);
         
        //Swapping starts
         
        s1 = s1 + s2;
         
        s2 = s1.substring(0, s1.length()-s2.length());
         
        s1 = s1.substring(s2.length());
         
        //Swapping ends
         
        System.out.println("After Swapping :");
         
        System.out.println("s1 : "+s1);
         
        System.out.println("s2 : "+s2);
    }   
}

```

## TextFileModificationProgram

```java
package CoreQuestion;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
 
public class TextFileModificationProgram
{   
    static void modifyFile(String filePath, String oldString, String newString)
    {
        File fileToBeModified = new File(filePath);
         
        String oldContent = "";
         
        BufferedReader reader = null;
         
        FileWriter writer = null;
         
        try
        {
            reader = new BufferedReader(new FileReader(fileToBeModified));
             
            //Reading all the lines of input text file into oldContent
             
            String line = reader.readLine();
             
            while (line != null) 
            {
                oldContent = oldContent + line + System.lineSeparator();
                 
                line = reader.readLine();
            }
             
            //Replacing oldString with newString in the oldContent
             
            String newContent = oldContent.replaceAll(oldString, newString);
             
            //Rewriting the input text file with newContent
             
            writer = new FileWriter(fileToBeModified);
             
            writer.write(newContent);
        }
        catch (IOException e)
        {
            e.printStackTrace();
        }
        finally
        {
            try
            {
                //Closing the resources
                 
                reader.close();
                 
                writer.close();
            } 
            catch (IOException e) 
            {
                e.printStackTrace();
            }
        }
    }
     
    public static void main(String[] args)
    {
        modifyFile("C:/StudentFile.txt", "85", "95");
         
        System.out.println("done");
    }
}
```

## concuracy

### AtomicIntegerExample

```java
package concuracy;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.atomic.AtomicInteger;

// No duplicated numbers; guaranteed to get to 10.
// However, order is still not guaranteed.
public class AtomicIntegerExample {
    private static AtomicInteger atomicCount = new AtomicInteger(0) ;
    
    public static void main(String[] args) {
        ExecutorService es = Executors.newFixedThreadPool(5);
        for(int i=1; i<=10; i++){
            es.submit(() -> System.out.print(atomicCount.incrementAndGet() + " "));
        }
        es.shutdown();
        
    }
}
// 2 5 3 1 4 6 7 8 9 10 
```

### BlockingQueueExample

```java
package concuracy;

import java.util.concurrent.BlockingQueue;
import java.util.concurrent.LinkedBlockingQueue;
import java.util.concurrent.TimeUnit;

public class BlockingQueueExample {
    public static void main(String[] args) {
        BlockingQueue<String> queue = new LinkedBlockingQueue<>();
        // regular Queue methods
        queue.offer("Red");
        queue.offer("Green");
        queue.offer("Blue");
        System.out.println(queue.poll());   // Red
        System.out.println(queue.peek());   // Green 
        System.out.println(queue);          // [Green, Blue]
        
        // special BlockingQueue methods
        try {
            // block is queue full...
            queue.offer("White", 100, TimeUnit.MILLISECONDS);
            // block is queue empty...
            queue.poll(200, TimeUnit.MILLISECONDS);
        } catch (InterruptedException ex) {
            ex.printStackTrace();
        }
        System.out.println(queue);          // [Blue, White]
        
    }
}

```

### CallableTest

```java
package concuracy;

import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;

// Illustrates how Callable, Executors, ExecutorService, and Future are related; 
// also shows how they work together to execute a task 
public class CallableTest {
    public static void main(String []args) {
        // create an ExecutorService with a fixed thread pool consisting of one thread
        ExecutorService es = Executors.newSingleThreadExecutor();
        
        // submit the Callable task (asynchronously) to the executor service 
        // and store the Future object 
        Future<Integer> future = es.submit(() -> 3 + 5); // V call()
        
        try {
            // get() will block for 500 msecs max. 
            // TimeUnit is an enum
            System.out.println("The answer is: "+future.get(500, TimeUnit.MILLISECONDS));
        } catch (InterruptedException | ExecutionException | TimeoutException ex) {
            ex.printStackTrace();
        }
        
        // shutdown the executor service otherwise this application will never terminate; 
        // existing tasks will be allowed to complete but no new tasks accepted
        es.shutdown();
    }
}

```

### CopyOnWriteCollections

```java
package concuracy;

import java.util.List;
import java.util.Set;
import java.util.concurrent.CopyOnWriteArrayList;
import java.util.concurrent.CopyOnWriteArraySet;

public class CopyOnWriteCollections {
    public static void main(String[] args) {
        List<String> names = new CopyOnWriteArrayList<>();
        names.add("Ann");
        names.add("Brian");
        names.add("Carol");
        
        // API: "The snapshot style iterator method uses a reference 
        //      to the state of the array at the point that the iterator was created. 
        //      This array never changes during the lifetime of the iterator, so 
        //      interference is impossible and the iterator is guaranteed not to throw 
        //      ConcurrentModificationException.". 
        for(String name:names){
            System.out.println(name);
            names.add(name);
        }
        System.out.println(names);
        System.out.println("--------------------------------------");

        Set<String> uniqueNames = new CopyOnWriteArraySet<>();
        uniqueNames.add("Ann");
        uniqueNames.add("Brian");
        uniqueNames.add("Carol");
        for(String name:uniqueNames){
            System.out.println(name);
            uniqueNames.add(name);
        }
        System.out.println(uniqueNames);
        System.out.println("Size is "+uniqueNames.size());
    }
    
}

```

## DataRace

```java
package concuracy;

public class DataRace {
    private static int count =0 ;
    
    public static void addToCounter(){
        int c = count;
        System.out.println("Before. "+count + ". Thread id: "+Thread.currentThread().getId());
        count = c + 1; // not atomic
        System.out.println("After. "+count + ". Thread id: "+Thread.currentThread().getId());
    } 
    public static void main(String[] args) {
        for(int i=1; i<=10; i++){
            new Thread(() -> addToCounter())
                    .start();
        }
    }
}
```

### Deadlock

```java
package concuracy;

// My thanks to Maaike van Putten (BrightBoost) for inspiring this example.
public class Deadlock {
    public static void go(){
        final String ransom    = "ransom";
        final String hostage   = "hostage";
        
        Thread criminals = new Thread( () -> {
            synchronized(hostage){
                System.out.println("The criminals have the hostage and want the ransom...");
                try {
                    Thread.sleep(500);
                } catch (InterruptedException ex) {
                    ex.printStackTrace();
                }
                // make sure this next block is inside the first synchronized block.
                synchronized(ransom){
                    System.out.println("The criminals have BOTH!");
                } // auto release of lock on 'ransom'
            } // auto release of lock on 'hostage'
        });

        Thread police = new Thread( () -> {
            synchronized(hostage){
                System.out.println("The police have the hostage and want the ransom...");
                try {
                    Thread.sleep(500);
                } catch (InterruptedException ex) {
                    ex.printStackTrace();
                }
                synchronized(ransom){
                    System.out.println("The police have BOTH!.");
                } // auto release of lock on 'hostage'
            } // auto release of lock on 'ransom'
        });
       
        criminals.start();
        police.start();
    }
    public static void main(String[] args) {
        go();
    }
    
}
```

### FixRaceWithLock

```java
package concuracy;

import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class FixRaceWithLock {
    private static int count =0 ;
    private static Lock lock = new ReentrantLock();
    
    public static void addToCounter(){
        if(lock.tryLock()){
            try{
//                lock.lock(); // blocking call
                int c = count;
                System.out.println("Before. "+count + ". Thread id: "+Thread.currentThread().getId());
                count = c + 1; // not atomic
                System.out.println("After. "+count + ". Thread id: "+Thread.currentThread().getId());
            } finally{
                lock.unlock();// return the lock
            }
        }else{
            // did not get the lock, do something else 
            System.out.println("Failed to get lock...");
        }
    } 

    public static void main(String[] args) {
        for(int i=1; i<=10; i++){
            new Thread(() -> addToCounter())
                    .start();
        }
    }
}

```

### FixRaceWithSynchronized

```java
package concuracy;

/*
// 1. 
        public synchronized static void addToCounter(){
// 2. 
        public static void addToCounter(){ 
            synchronized(FixRaceWithSynchronized.class){   
// 3. 
        synchronized(lock){   
// 4. 
        synchronize on 'this'
//          - make addToCounter() an instance method
//          - synchronized(this) inside the method
//          - create an instance of the overall class FixRaceWithSynchronized in main()
//          - ensure that all the threads share the same instance!
*/
public class FixRaceWithSynchronized {
    private static Object lock = new Object();
    private static int count =0 ;
    
//    public synchronized static void addToCounter(){ 
//    public static void addToCounter(){ 
////        synchronized(FixRaceWithSynchronized.class){   
//        synchronized(lock){   
//            int c = count;
//            System.out.println("Before. "+count + ". Thread id: "+Thread.currentThread().getId());
//            count = c + 1; // not atomic
//            System.out.println("After. "+count + ". Thread id: "+Thread.currentThread().getId());
//        }
//    } 
    public synchronized void addToCounter(){
//        synchronized(this){
            int c = count;
            System.out.println("Before. "+count + ". Thread id: "+Thread.currentThread().getId());
            count = c + 1; // not atomic
            System.out.println("After. "+count + ". Thread id: "+Thread.currentThread().getId());
//        }
    } 

    public static void main(String[] args) {
        // When synch. on 'this' make sure all threads use the same instance.
        FixRaceWithSynchronized instance = new FixRaceWithSynchronized();
        for(int i=1; i<=10; i++){
            new Thread(() -> instance.addToCounter())
//            new Thread(() -> addToCounter())
                    .start();
        }
    }
}

```

### RaceCondition

```java
package concuracy;

import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

class BankAccount{
    private int balance = 50;
    public int getBalance() {
        return balance;
    }
    public void withdraw(int balance) {
        this.balance -= balance;
    }    
}
public class RaceCondition implements Runnable {
    private static Lock lock = new ReentrantLock();
    
    // There is ONLY ONE BankAccount! It is shared between the two threads.
    private BankAccount acct = new BankAccount();
    public static void main(String []args){
        Runnable r = new RaceCondition();   // only 1 instance
        Thread john = new Thread(r);        // BOTH threads share the 1 instance
        Thread mary = new Thread(r);
        john.setName("John");
        mary.setName("Mary");
        john.start();
        mary.start();
    }

    @Override
    public void run() {
        for(int i=1; i<=5; i++){
            makeWithdrawal(10);
            if(acct.getBalance() < 0){
                System.out.println("Account is overdrawn!");
            }
            try{
                Thread.sleep(500);
            }catch (InterruptedException ie){}
        }
    }

//    private synchronized void makeWithdrawal(int amtToWithdraw){
////    private void makeWithdrawal(int amtToWithdraw){
//        if(acct.getBalance() >= amtToWithdraw){
//            System.out.println(Thread.currentThread().getName()
//                + ". Balance BEFORE: " + acct.getBalance());
//            try{
//                
//                Thread.sleep(500);
//            }catch (InterruptedException ie){}
//            acct.withdraw(amtToWithdraw);
//            System.out.println(Thread.currentThread().getName()
//                    + ". Balance AFTER: " + acct.getBalance());
//        }else{
//            System.out.println(Thread.currentThread().getName() + " is unable to withdraw "
//                    + "as balance is: " + acct.getBalance());
//        }
//    }

    // using Lock
    
    private void makeWithdrawal(int amtToWithdraw){
        try{
            lock.lock(); // blocking call; one thread gets in, others wait
            if(acct.getBalance() >= amtToWithdraw){
                System.out.println(Thread.currentThread().getName()
                    + ". Balance BEFORE: " + acct.getBalance());
                try{

                    Thread.sleep(500);
                }catch (InterruptedException ie){}
                acct.withdraw(amtToWithdraw);
                System.out.println(Thread.currentThread().getName()
                        + ". Balance AFTER: " + acct.getBalance());
            }else{
                System.out.println(Thread.currentThread().getName() + " is unable to withdraw "
                        + "as balance is: " + acct.getBalance());
            }
        } finally{
            lock.unlock();
        }
    }

}
```

### RunnableTest

```java
package concuracy;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class RunnableTest {
    public static void main(String []args) {
        // create an ExecutorService with a fixed thread pool consisting of one thread
        ExecutorService es = Executors.newSingleThreadExecutor();
        
        // execute the Runnable task (asynchronously) - void run()
        es.execute(() -> System.out.println("Runnable example")); 
        
        // shutdown the executor service otherwise this application will never terminate; 
        // existing tasks will be allowed to complete but no new tasks accepted
        es.shutdown();
    }
}

```

### ScheduledExecutors

```java
package concuracy;

import java.util.concurrent.ExecutionException;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class ScheduledExecutors {
    private static ScheduledExecutorService schedES = Executors.newScheduledThreadPool(10);
    
    public static void main(String[] args) {
//        schedule();
//        scheduleWithFixedDelay();
        scheduleAtFixedRate();
    }
    public static void schedule(){
        System.out.println("Start...");
        Future<String> future = schedES.schedule(() -> "A", 2, TimeUnit.SECONDS);
        try {
            System.out.println(future.get()); // block
        } catch (InterruptedException | ExecutionException ex) {
            ex.printStackTrace();
        }  finally{
            schedES.shutdown();
        }
        System.out.println("Always at the end!");
    }
    public static void scheduleWithFixedDelay(){
        System.out.println("Start...");
        // 300 msecs is the time to wait from when the previous task finishes to starting the next task
        //  => previous task finishes - wait 300msecs - start next task
        final long INITIAL_DELAY = 2000, WAIT_PERIOD_AFTER_PREVIOUS_TASK_FINISHED=300;
        schedES.scheduleWithFixedDelay(() -> System.out.println("Thread id: "+Thread.currentThread().getId()), 
                                       INITIAL_DELAY, WAIT_PERIOD_AFTER_PREVIOUS_TASK_FINISHED, TimeUnit.MILLISECONDS);
       // schedES.shutdown(); // if I shut it down, nothing happens
    }
    public static void scheduleAtFixedRate(){
        System.out.println("Start...");
        // Assuming 500 msecs is the time after the initial delay to wait to start the next task and so forth
        //  => initial task starts at 2000msecs                 = 2000msecs
        //       task 2 starts at 2000msecs + 500 msecs         = 2500msecs
        //       task 3 starts at 2000msecs + (500 msecs * 2)   = 3000msecs
        //       task 4 starts at 2000msecs + (500 msecs * 3)   = 3500msecs and so on...
        final long INITIAL_DELAY = 2000, WAIT_PERIOD_BEFORE_STARTING_NEXT_TASK=300;
        schedES.scheduleAtFixedRate(() ->   System.out.println("Thread id: "+Thread.currentThread().getId()), 
                                            INITIAL_DELAY, WAIT_PERIOD_BEFORE_STARTING_NEXT_TASK, TimeUnit.MILLISECONDS);
        //schedES.shutdown(); // if I shut it down, nothing happens
    }
}

```

### SkipListCollections

```java
package concuracy;

import java.util.Map;
import java.util.Set;
import java.util.concurrent.ConcurrentSkipListMap;
import java.util.concurrent.ConcurrentSkipListSet;

public class SkipListCollections {
    public static void main(String[] args) {
        Set<String> countries = new ConcurrentSkipListSet<>();
        countries.add("Germany");
        countries.add("Canada");
        countries.add("Australia");
        
        // natural order for Stringa is alphabetic
        for(String country:countries){
            System.out.println(country);
        }

        Map<String, Integer> map = new ConcurrentSkipListMap<>();
        map.put("Jack", 12);
        map.put("Zack", 15);
        map.put("Anna", 22);
        
        // ordered by keys
        for(String key:map.keySet()){
            System.out.println(key + " -> " + map.get(key));
        }
    }
}

```

### SubmittingTaskCollections

```java
package concuracy;

import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class SubmittingTaskCollections {
    // Single Thread Executors will accept tasks sequentially in the order
    // they are submitted
//    private static ExecutorService es = Executors.newSingleThreadExecutor();
    // with 4 threads to share the work, there is no guarantee which letter
    // will appear first
    private static ExecutorService es = Executors.newFixedThreadPool(4);
    private static List<Callable<String>> callables = new ArrayList<>();
    
    public static void main(String[] args) {
        callables.add(() -> "A"); // adding Callable tasks
        callables.add(() -> "B");
        callables.add(() -> "C");
        callables.add(() -> "D");

       // invokeAny();
        invokeAll();
    }
    public static void invokeAny(){
        try {
            // submitting a collection of tasks
            // executes synchronously and returns when one of the tasks has completed, all
            // other tasks are cancelled
            // Note: Single thread executor will always execute the first task submitted.
            String result = es.invokeAny(callables); // TimeUnit overloaded version exists
            System.out.println(result);
        } catch (InterruptedException | ExecutionException ex) {
            ex.printStackTrace();
        } finally{
            // don't forget to shutdown the executor
            // finally always executes
            es.shutdown();;
        }
        System.out.println("Always at the end!");
    }
    
    public static void invokeAll(){
        try {
            // submitting a collection of tasks
            // executes synchronously and returns when all of the tasks are completed
            // order is maintained i.e. the result for callables.get(0) goes into list.get(0)
            List<Future<String>> list = es.invokeAll(callables); // TimeUnit overloaded version exists
            for(Future<String> future:list){
                System.out.println(future.get());// A, B, C, D in order
            }
        } catch (InterruptedException | ExecutionException ex) {
            ex.printStackTrace();
        } finally{
            // don't forget to shutdown the executor
            // finally always executes
            es.shutdown();;
        }
        System.out.println("Always at the end!");
    }
}

```

### SynchronizedCollection

```java
package concuracy;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class SynchronizedCollection {
    public static void main(String[] args) {
        List<String> dogTypes = new ArrayList<>();
        dogTypes.add("German Shepherd");
        dogTypes.add("Labrador");
        List<String> dogTypesSyn = Collections.synchronizedList(dogTypes);
        
        // safe to use dogTypesSyn with multiple threads...
    }
    
}

```

### TheProblem

```java
package concuracy;

import java.util.HashMap;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

public class TheProblem {
    public static void main(String[] args) {
        iteratorNoIssue();
        //enhancedForIssue();
    }
    public static void iteratorNoIssue(){
        Map<String, String> capitalCities = new HashMap<>();
        capitalCities.put("Oslo", "Norway");
        capitalCities.put("Copenhagen", "Denmark");

        System.out.println("Before: "+capitalCities);
        for (var iter = capitalCities.keySet().iterator(); iter.hasNext(); ) {
            var key = iter.next();
            System.out.println(key + " is the capital of " + capitalCities.get(key));
            iter.remove();
        }
        System.out.println("After: "+capitalCities);
    }
    public static void enhancedForIssue(){
        Map<String, String> capitalCities = new HashMap<>();
//        Map<String, String> capitalCities = new ConcurrentHashMap<>(); // fixes the issue
        capitalCities.put("Oslo", "Norway");
        capitalCities.put("Copenhagen", "Denmark");
        
        System.out.println("Before: "+capitalCities);
        for(String key: capitalCities.keySet()){
            System.out.println(key+ " is the capital of "+capitalCities.get(key));
            capitalCities.remove(key);// ConcurrentModificationException
        }
        System.out.println("After: "+capitalCities);
    }
}

```

## CompletableFuture

### ExceptionUtil

```java
package CompletableFuture;

import java.util.function.BiConsumer;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Supplier;

public class ExceptionUtil {

    @FunctionalInterface
    public interface FunctionWithException<T, R, E extends Exception>{
        R apply(T t)throws E;
    }

    public static<T, R, E extends Exception> Function<T, R> rethrowFunction(FunctionWithException<T, R, E> function){
        return t->{
            try{ return function.apply(t);}
             catch (Exception exception) {
                throwAsUnchecked(exception);
                return null;
            }
        };
    }

    @SuppressWarnings("unchecked")
    private static <E extends Throwable> void throwAsUnchecked(Exception exception) throws E{
        throw (E) exception;
    }

    @FunctionalInterface
    public interface SupplierWithException<R, E extends Exception>{
        R get() throws E;
    }

    public static <T, E extends Exception> Supplier<T> rethrowSupplier(SupplierWithException<T, E> function){
        return ()->{
            try{ return function.get();}
            catch (Exception exception) {
                throwAsUnchecked(exception);
                return null;
            }
        };
    }

    @FunctionalInterface
    public interface ConsumerWithExceptions<R, E extends Exception>{
        void accept(R r)throws E;
    }

    public static <T, E extends Exception> Consumer<T> rethrowConsumer(ConsumerWithExceptions<T, E> consumer){
        return t->{
            try{ consumer.accept(t);}
            catch (Exception exception) {
                throwAsUnchecked(exception);
            }
        };
    }

    @FunctionalInterface
    public interface BiConsumerWithExceptions<T, U, E extends Exception>{
        void accept(T t, U u) throws E;
    }

    public static <T, U, E extends Exception> BiConsumer<T, U> rethrowBiConsumer(BiConsumerWithExceptions<T, U, E> biConsumer){
        return (t, u)->{
            try{ biConsumer.accept(t, u);}
            catch (Exception exception) {
                throwAsUnchecked(exception);
            }
        };
    }


}
```

### QueryResult

```java
package CompletableFuture;

import java.io.Serializable;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public final class QueryResult implements Serializable {

    private final ResultType type;
    private final Object data;
    private final Map<String, Object> metadata;

    public QueryResult(Object data, ResultType type) {
        this.data = data;
        this.type=type;
        this.metadata=new HashMap<>();
    }

    public static QueryResult from(Object obj){
        if(obj==null){
            return new QueryResult(null, ResultType.NOTHING);
        }

        if(obj instanceof Exception || obj instanceof Exception){
            return new QueryResult(obj, ResultType.EXCEPTION);
        }

        if(obj instanceof List<?>){
            return new QueryResult(obj, ResultType.COLLECTION);
        }

        return new QueryResult(obj, ResultType.OBJECT);
    }

    public QueryResult addMeta(String key, Object value){
        metadata.put(key,value);
        return this;
    }

    public QueryResult withCount(long count){
        return addMeta("count", count);
    }

    @Override
    public String toString(){ return type.name()+": "+data.toString();}

    public ResultType getType() {
        return type;
    }

    public Object getData() {
        return data;
    }

    public Map<String, Object> getMetadata() {
        return metadata;
    }

    public enum ResultType{
        COLLECTION,
        EXCEPTION,
        NOTHING,
        OBJECT
    }
}

```

## completable

### CompletableFutureExample

```java
package completable;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.TimeUnit;

public class CompletableFutureExample {
    public static void main(String args[])throws InterruptedException, ExecutionException{
        runAsync();
        supplyAsync();
        thenApply();
        thenAccept();
        System.out.println("Main thread");
    }

    public static void runAsync()throws InterruptedException, ExecutionException{
        CompletableFuture<Void> async=CompletableFuture.runAsync(()->{
           try {
               TimeUnit.SECONDS.sleep(1);
               System.out.println("Running in a separate thread than the main thread.");
           }catch (InterruptedException e){
               throw new IllegalStateException(e);
           }

        });
        System.out.println("runAsync Blocking 1");
        async.get();
        System.out.println("runAsync Blocking 2");
    }
    public static void supplyAsync()throws InterruptedException, ExecutionException{
        CompletableFuture<String> async=CompletableFuture.supplyAsync(()->{
            try {
                TimeUnit.SECONDS.sleep(1);
                System.out.println("Running in a separate thread than the main thread.");
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
            return "Eazy Bytes";
        });
        System.out.println("supplyAsync Blocking 1");
        String result=async.get();
        System.out.println(result);
        System.out.println("supplyAsync Blocking 2");
    }

    public static void thenApply()throws InterruptedException, ExecutionException{
        CompletableFuture<String> future=CompletableFuture.supplyAsync(()->{
            try {
                TimeUnit.SECONDS.sleep(1);
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
            return "Eazy";
        });

        System.out.println("thenApply middle block");

        CompletableFuture<String> finalFuture=future.thenApply(name->{
            try {
                TimeUnit.SECONDS.sleep(1);
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
            return name+" Bytes";
        });

        System.out.println("thenApply before final block");
        System.out.println(finalFuture.get());
        System.out.println("thenApply Blocking");
    }

    public static void thenAccept()throws InterruptedException, ExecutionException{
        CompletableFuture<String> future=CompletableFuture.supplyAsync(()->{
            try {
                TimeUnit.SECONDS.sleep(1);
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
            return "Accept";
        });

        System.out.println("thenApply middle block");

        future.thenAccept(result->{
            try {
                TimeUnit.SECONDS.sleep(1);
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
            System.out.println("Received the value"+result);
        });
        System.out.println("thenAccept before final block");
        future.get();
        System.out.println("thenAccept Blocking");
    }

}
```

### CompletableFutureExample1

```java
package completable;

import java.util.Arrays;
import java.util.List;  
import java.util.concurrent.CompletableFuture;

public class CompletableFutureExample1 {
    public static void main(String[] args) {
        try
        {
            List<Integer> list = Arrays.asList(5,9,14);
            list.stream().map(num->CompletableFuture.supplyAsync(()->getNumber(num)))
                    .map(CompletableFuture->CompletableFuture.thenApply(n->n*n))
                    .map(t->t.join()).forEach(s->System.out.println(s));
        }
        catch (Exception e)
        {
            e.printStackTrace();
        }
    }
    private static int getNumber(int a) {
        return a*a;
    }
} 
```

### DZoneCompleatableExamples

```java
package completable;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.TimeUnit;

public class DZoneCompleatableExamples {
    public static void main(String args[]){

    }
    static void completedFutureExample() {
        CompletableFuture<String> cf = CompletableFuture.completedFuture("message");
        boolean flag=cf.isDone();
        System.out.println(cf.getNow(null));
    }

    static void runAsyncExample()throws InterruptedException, ExecutionException {
        CompletableFuture<Void> cf = CompletableFuture.runAsync(() -> {
            try {
                System.out.println(Thread.currentThread().isDaemon());
                TimeUnit.SECONDS.sleep(1);
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
        });
        System.out.println("is done"+cf.isDone());
        cf.get();
        System.out.println("is done"+cf.isDone());
    }

    static void thenApplyExample() {
        CompletableFuture<String> cf = CompletableFuture.completedFuture("message").thenApply(s -> {
            System.out.println(Thread.currentThread().isDaemon());
            return s.toUpperCase();
        });
        System.out.println(cf.getNow(null));
    }

    static void thenApplyAsyncExample() {
        CompletableFuture<String> cf = CompletableFuture.completedFuture("message").thenApplyAsync(s -> {
            try {
                System.out.println(Thread.currentThread().isDaemon());
                TimeUnit.SECONDS.sleep(1);
                return s.toUpperCase();
            }catch (InterruptedException e){
                throw new IllegalStateException(e);
            }
        });
        System.out.println(cf.getNow(null));
        System.out.println(cf.join());
    }
}

```

### GFG

```java
package completable;

import java.util.concurrent.*;
  
class GFG { 
    public static void main(String[] args) throws Exception 
    { 
        CompletableFuture<String> greetingFuture 
            = CompletableFuture.supplyAsync(() -> { 
                  // some async computation 
                  return "Hello from CompletableFuture"; 
              }); 
  
        System.out.println(greetingFuture.get()); 
    } 
}
```

### GFGCombine

```java
package completable;/*package whatever //do not write package name here */
  
import java.util.concurrent.*; 
  
class GFGCombine { 
    public static void main(String[] args) throws Exception 
    { 
        CompletableFuture<String> helloFuture 
            = CompletableFuture.supplyAsync(() -> "Hello"); 
        CompletableFuture<String> greetingFuture 
            = CompletableFuture.supplyAsync(() -> "World"); 
  
        CompletableFuture<String> combinedFuture 
            = helloFuture.thenCombine( 
                greetingFuture, (m1, m2) -> m1 + " " + m2); 
  
        System.out.println(combinedFuture.get());
    } 
}
```

### GFGExceptinHandling

```java
package completable;

import java.util.concurrent.*;
  
class GFGExceptinHandling { 
    public static void main(String[] args) throws Exception 
    { 
        CompletableFuture<Integer> resultFuture 
          // java.lang.ArithmeticException: / by zero 
            = CompletableFuture.supplyAsync(() -> 10 / 0)   
                      .exceptionally(ex -> 0); 
        
          // 0 - returned by exceptionally block 
        System.out.println(resultFuture.get()); 
    } 
}
```

## Collector

### CollectorOperation

```java
package Collector;

import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectorOperation {
    public static void main(String args[]){
        List<Student> studentList = new ArrayList<>();

        studentList.add(new Student("Paul", 11, "Economics", 78.9));
        studentList.add(new Student("Zevin", 12, "Computer Science", 91.2));
        studentList.add(new Student("Harish", 13, "History", 83.7));
        studentList.add(new Student("Xiano", 14, "Literature", 71.5));
        studentList.add(new Student("Soumya", 15, "Economics", 77.5));
        studentList.add(new Student("Asif", 16, "Mathematics", 89.4));
        studentList.add(new Student("Nihira", 17, "Computer Science", 84.6));
        studentList.add(new Student("Mitshu", 18, "History", 73.5));
        studentList.add(new Student("Vijay", 19, "Mathematics", 92.8));
        studentList.add(new Student("Harry", 20, "History", 71.9));

        //Collectors.toList() :
        //It returns a Collector which collects all input elements into a new List.
        // Example : Collecting top 3 performing students into List
        collectorToList(studentList);

        //Collectors.toSet() :
        //It returns a Collector which collects all input elements into a new Set.
        // Example : Collecting subjects offered into Set.
        collectorsToSet(studentList);

        //Collectors.toMap() :
        //This method returns a Collector which collects input elements into a Map whose keys and values are the result of applying mapping functions to input elements.
        //Example : Collecting name and percentage of each student into a Map
        collectorsToMap(studentList);

        //Collectors.toCollection() :
        //This method returns a Collector which collects all input elements into a new Collection.
        //Example : Collecting first 3 students into LinkedList
        collectorsToCollection(studentList);

        //Collectors.joining() :
        //This method returns a Collector which concatenates input elements separated by the specified delimiter.
        //Example : Collecting the names of all students joined as a string
        collectorsJoining(studentList);

        //Collectors.counting() :
        //It returns a Collector that counts number of input elements.
        //Example : Counting number of students.
        collectorsCounting(studentList);

        //Collectors.maxBy() :
        //This method returns a Collector that collects largest element in a stream according to supplied Comparator.
        //Example : Collecting highest percentage.
        collectorsMaxBy(studentList);

        //Collectors.minBy() :
        //This method returns a Collector which collects smallest element in a stream according to supplied Comparator.
        //Example : Collecting lowest percentage.
        collectorsMinBy(studentList);

        //summingInt(), summingLong(), summingDouble()
        //These methods returns a Collector which collects sum of all input elements.
        //Example : Collecting sum of percentages
        summingInt(studentList);
        summingLong(studentList);
        summingDouble(studentList);

        //averagingInt(), averagingLong(), averagingDouble()
        //These methods return a Collector which collects average of input elements.
        //Example : Collecting average percentage
        averagingInt(studentList);
        averagingLong(studentList);
        averagingDouble(studentList);

        //summarizingInt(), summarizingLong(), summarizingDouble()
        //These methods return a special class called Int/Long/ DoubleSummaryStatistics which contain statistical information like sum, max, min, average etc of input elements.
        //Example : Extracting highest, lowest and average of percentage of students
        summarizingDouble(studentList);

        //Collectors.groupingBy() :
        //This method groups the input elements according supplied classifier and returns the results in a Map.
        //Example : Grouping the students by subject
        collectorsGroupingBy(studentList);

        //Collectors.partitioningBy() :
        //This method partitions the input elements according to supplied Predicate and returns a Map<Boolean, List<T>>. Under the true key, you will find elements which match given Predicate and under the false key, you will find the elements which doesn’t match given Predicate.
        //Example : Partitioning the students who got above 80.0% from who don’t.
        collectorsPartitioningBy(studentList);

        //Collectors.collectingAndThen() :
        //This is a special method which lets you to perform one more action on the result after collecting the result.
        //Example : Collecting first three students into List and making it unmodifiable
        collectorsCollectingAndThen(studentList);

    }

    public static void collectorToList(List<Student> studentList){

        List<Student> top3Students=studentList.stream().sorted(Comparator.comparingDouble(Student::getPercentage).reversed()).limit(3).collect(Collectors.toList());
        System.out.println(top3Students);
    }

    public static void collectorsToSet(List<Student> studentList){

        Set<String> subjects=studentList.stream().map(s->s.getSubject()).collect(Collectors.toSet());
        //Set<String> subjects = studentList.stream().map(Student::getSubject).collect(Collectors.toSet());
        System.out.println(subjects);
    }

    public static void collectorsToMap(List<Student> studentList){

        Map<String,Double> mapStNamePercentage=studentList.stream().collect(Collectors.toMap(Student::getName,Student::getPercentage));
        Map<String,Double> mapStNamePercentage1=studentList.stream().collect(Collectors.toMap(s->s.getName(),s->s.getPercentage()));
        System.out.println(mapStNamePercentage);
        System.out.println(mapStNamePercentage1);
    }

    public static void collectorsToCollection(List<Student> studentList){

        LinkedList<Student> first3Students=studentList.stream().limit(3)
                .collect(Collectors.toCollection(LinkedList::new));
        System.out.println(first3Students);
    }

    public static void collectorsJoining(List<Student> studentList){

        String names=studentList.stream().map(s->s.getName()).collect(Collectors.joining(", "));
        System.out.println(names);
    }

    public static void collectorsCounting(List<Student> studentList){

        Long count=studentList.stream().collect(Collectors.counting());
        System.out.println(count);
    }

    public static void collectorsMaxBy(List<Student> studentList){

        Optional<Double> highestPercent=studentList.stream().map(Student::getPercentage).collect(Collectors.maxBy(Comparator.naturalOrder()));
        System.out.println(highestPercent);
    }

    public static void collectorsMinBy(List<Student> studentList){

        Optional<Double> highestPercent=studentList.stream().map(Student::getPercentage).collect(Collectors.minBy(Comparator.naturalOrder()));
        System.out.println(highestPercent);
    }

    public static void summingInt(List<Student> studentList){

        Integer summingInt=studentList.stream().collect(Collectors.summingInt(s->s.getId()));
        System.out.println(summingInt);
    }

    public static void summingLong(List<Student> studentList){

        Long sumingLong=studentList.stream().collect(Collectors.summingLong(s->s.getId()));
        System.out.println(sumingLong);
    }

    public static void summingDouble(List<Student> studentList){

        Double summingDouble=studentList.stream().collect(Collectors.summingDouble(s->s.getPercentage()));
        System.out.println(summingDouble);
    }

    public static void averagingInt(List<Student> studentList){

        Double averagingInt=studentList.stream().collect(Collectors.averagingInt(s->s.getId()));
        System.out.println(averagingInt);
    }

    public static void averagingLong(List<Student> studentList){

        Double averagingLong=studentList.stream().collect(Collectors.averagingLong(s->s.getId()));
        System.out.println(averagingLong);
    }

    public static void averagingDouble(List<Student> studentList){

        Double averagingDouble=studentList.stream().collect(Collectors.averagingDouble(s->s.getPercentage()));
        System.out.println(averagingDouble);
    }

    public static void summarizingDouble(List<Student> studentList){

        DoubleSummaryStatistics studentStats = studentList.stream().collect(Collectors.summarizingDouble(Student::getPercentage));

        System.out.println("Highest Percentage : "+studentStats.getMax());

        System.out.println("Lowest Percentage : "+studentStats.getMin());

        System.out.println("Average Percentage : "+studentStats.getAverage());

        System.out.println("Sum : "+studentStats.getSum());

        System.out.println("Count : "+studentStats.getCount());
    }
    public static void collectorsGroupingBy(List<Student> studentList){

        Map<String,List<Student>> groupBySubject=studentList.stream().collect(Collectors.groupingBy(s->s.getSubject()));
        System.out.println(groupBySubject);
    }

    public static void collectorsPartitioningBy(List<Student> studentList){

        Map<Boolean,List<Student>> partitioningBy=studentList.stream().collect(Collectors.partitioningBy(s->(s.getPercentage()>80)));
        System.out.println(partitioningBy);
    }

    public static void collectorsCollectingAndThen(List<Student> studentList){

        List<Student> first3Students = studentList.stream().limit(3)
                .collect(Collectors.collectingAndThen(Collectors.toList(),
                        Collections::unmodifiableList));

        System.out.println(first3Students);

        // Create an Immutable Set
        Set<String> st
                = Stream.of("GEEKS", "FOR", "GEEKS").collect(
                        Collectors.collectingAndThen(Collectors.toSet(),
                                        Collections::<String>unmodifiableSet));
        System.out.println(st);

        // Create an Immutable Map
        Map<String, String> mp
                = Stream
                .of(new String[][] {
                        { "1", "Geeks" },
                        { "2", "For" },
                        { "3", "Geeks" } })
                .collect(Collectors.collectingAndThen(
                                        Collectors.toMap(p -> p[0], p -> p[1]),
                                        Collections::<String, String> unmodifiableMap));
        System.out.println(mp);
    }

}
```

### Student

```java
package Collector;

class Student
{
    String name;

    int id;

    String subject;

    double percentage;

    public Student(String name, int id, String subject, double percentage)
    {
        this.name = name;
        this.id = id;
        this.subject = subject;
        this.percentage = percentage;
    }

    public String getName()
    {
        return name;
    }

    public int getId()
    {
        return id;
    }

    public String getSubject()
    {
        return subject;
    }

    public double getPercentage()
    {
        return percentage;
    }

    @Override
    public String toString()
    {
        return name+"-"+id+"-"+subject+"-"+percentage;
    }
}
```

## Character

### ConvertingCharArrayToListInJava

```java
package Character;

import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class ConvertingCharArrayToListInJava {
    public static void main(String args[]){
        String s = "asdasdasda";
        s.chars().mapToObj(c -> (char) c).collect(Collectors.toList());

        char[] chars = s.toCharArray();
        //      List<Character> list = Arrays.asList(chars); // this does not compile,
        List<char[]> asList = Arrays.asList(chars); // because this DOES compile.
        List<Character> listC = new ArrayList<>();
        for (char c : chars) {
            listC.add(c);
        }
        //And this is how you convert List back to array:
        Character[] array = listC.toArray(new Character[listC.size()]);


        char[] myCharArray = { 'H', 'e', 'l', 'l', 'o', '-', 'X', 'o', 'c', 'e' };

        Stream<Character> myStreamOfCharacters = IntStream
                .range(0, myCharArray.length)
                .mapToObj(i -> myCharArray[i]);

        List<Character> myListOfCharacters = myStreamOfCharacters.collect(Collectors.toList());

        myListOfCharacters.forEach(System.out::println);

        List<Character> list = s.chars().mapToObj( c -> (char)c).collect(Collectors.toList());

        ArrayList<Character> characterList
                = (ArrayList<Character>) s.chars().mapToObj(c -> (char)c).collect(Collectors.toList());

        HashSet<Character> abc =
                (HashSet<Character>) s.chars().mapToObj(c -> (char)c).collect(Collectors.toSet());

        //To get Characters in a specific range from given String
        s.chars().filter(a -> a > 118).mapToObj(c -> (char)c).forEach(a -> System.out.println(a));

        List<Character> characterLst = String.valueOf(chars).chars().mapToObj(i -> (char) i).collect( Collectors.toList() );

        List strList = Stream.of( s.toCharArray() ).map( String::valueOf ).collect( Collectors.toList() );

        List<Character> charlist = String.copyValueOf(myCharArray)
                .chars()
                .mapToObj(i -> (char) i)
                .collect(Collectors.toList());



        StringBuffer st = new StringBuffer("Mike is good");
        System.out.println(replaceWhitespaces(st.toString(), "%20"));
    }

    private static String replaceWhitespaces(String string, String replacement) {
        return string != null ? string.replaceAll("\\s", replacement) : null;


    }
}
```

## airlinetest

### CeilingExample

```java
package airlinetest;

public class CeilingExample {

    public static int findCeiling(int num, int divisor) {
        return (num + divisor - 1) / divisor;
    }

    public static void main(String[] args) {
        int number = 7;
        int divisor = 3;
        int ceiling = findCeiling(number, divisor);

        System.out.println("Ceiling of " + number + " with divisor " + divisor + " is: " + ceiling);
    }
}
```

### ColorSlots

```java
package airlinetest;

import java.util.ArrayList;
import java.util.List;

public class ColorSlots {

    public static void main(String[] args) {
        List<String> slots = new ArrayList<>();
        slots.add("s1");
        slots.add("s2");
        slots.add("s3");
        slots.add("s4");

        String[] colors = {"R", "B", "G"};

        int colorIndex = 0;

        // Iterate through available slots and assign colors
        for (String slot : slots) {
            String color = colors[colorIndex];
            System.out.println("Assign color " + color + " to slot " + slot);

            // Move to the next color (cycling through colors)
            colorIndex = (colorIndex + 1) % colors.length;
        }
    }
}
```

### ColorSlotsLinkedList

```java
package airlinetest;

class SlotNode {
    String slot;
    String color;
    SlotNode next;

    public SlotNode(String slot, String color) {
        this.slot = slot;
        this.color = color;
        this.next = null;
    }
}

public class ColorSlotsLinkedList {

    public static void main(String[] args) {
        // Create slots and colors
        String[] slots = {"s1", "s2", "s3", "s4"};
        String[] colors = {"R", "B", "G"};

        // Create a cyclic linked list
        SlotNode head = createCyclicLinkedList(slots, colors);

        // Iterate through available slots and assign colors
        iterateAndAssignColors(head, slots.length);
    }

    private static SlotNode createCyclicLinkedList(String[] slots, String[] colors) {
        SlotNode head = new SlotNode(slots[0], colors[0]);
        SlotNode current = head;

        // Create a cyclic linked list
        for (int i = 1; i < slots.length; i++) {
            SlotNode newNode = new SlotNode(slots[i], colors[i % colors.length]);
            current.next = newNode;
            current = newNode;
        }

        // Make the linked list cyclic
        current.next = head;

        return head;
    }

    private static void iterateAndAssignColors(SlotNode head, int iterations) {
        SlotNode current = head;

        // Iterate through the cyclic linked list and assign colors
        for (int i = 0; i < iterations; i++) {
            System.out.println("Assign color " + current.color + " to slot " + current.slot);
            current = current.next;
        }
    }
}

```

### FindDuplicates

```java
package airlinetest;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class FindDuplicates {

    public static List<Integer> findDuplicates(int[] nums) {
        List<Integer> result = new ArrayList<>();
        Map<Integer, Integer> frequencyMap = new HashMap<>();

        // Count the frequency of each element
        for (int num : nums) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }

        // Check for elements with frequency greater than 1
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            if (entry.getValue() > 1) {
                result.add(entry.getKey());
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int[] array = {4, 3, 2, 7, 8, 2, 3, 1};

        List<Integer> duplicates = findDuplicates(array);

        System.out.println("Duplicates in the array: " + duplicates);
    }
}
```

### FirstLastPositionInSortedArray

```java
package airlinetest;

public class FirstLastPositionInSortedArray {

    public static int[] searchRange(int[] nums, int target) {
        int firstPosition = findFirstPosition(nums, target);
        int lastPosition = findLastPosition(nums, target);

        return new int[]{firstPosition, lastPosition};
    }

    private static int findFirstPosition(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        int result = -1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] >= target) {
                result = mid;
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }

        return result;
    }

    private static int findLastPosition(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        int result = -1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] <= target) {
                result = mid;
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int[] array = {5, 7, 7, 8, 8, 10};
        int target = 8;

        int[] result = searchRange(array, target);

        System.out.println("First and Last Position of " + target + ": [" + result[0] + ", " + result[1] + "]");
    }
}
```

### FlightStatusTracker

```java
package airlinetest;

import java.time.LocalDateTime;
import java.util.HashMap;
import java.util.Map;

public class FlightStatusTracker {
    public static void main(String[] args) {
        // Create a Map to store flight statuses
        Map<LocalDateTime, String> flightStatusMap = new HashMap<>();

        // Add entries for each hour
        flightStatusMap.put(LocalDateTime.of(2022, 2, 16, 12, 0), "On time");
        flightStatusMap.put(LocalDateTime.of(2022, 2, 16, 13, 0), "Delayed");
        flightStatusMap.put(LocalDateTime.of(2022, 2, 16, 14, 0), "On time");

        // Retrieve flight status for a specific hour
        LocalDateTime targetTime = LocalDateTime.of(2022, 2, 16, 13, 0);
        String status = flightStatusMap.getOrDefault(targetTime, "No data available");

        System.out.println("Flight status at " + targetTime + ": " + status);
    }
}
```

### FlipImage

```java
package airlinetest;

public class FlipImage {

    public static int[][] flipAndInvertImage(int[][] image) {
        for (int[] row : image) {
            reverseArray(row);
            invertArray(row);
        }
        return image;
    }

    private static void reverseArray(int[] array) {
        int start = 0;
        int end = array.length - 1;

        while (start < end) {
            // Swap elements using XOR
            array[start] ^= array[end];
            array[end] ^= array[start];
            array[start] ^= array[end];

            start++;
            end--;
        }
    }

    private static void invertArray(int[] array) {
        for (int i = 0; i < array.length; i++) {
            // Invert values using XOR
            array[i] ^= 1;
        }
    }

    public static void printImage(int[][] image) {
        for (int[] row : image) {
            for (int pixel : row) {
                System.out.print(pixel + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int[][] image = {
            {1, 0, 1},
            {0, 1, 0},
            {1, 1, 1}
        };

        System.out.println("Original Image:");
        printImage(image);

        flipAndInvertImage(image);

        System.out.println("\nFlipped and Inverted Image:");
        printImage(image);
    }
}
```

### FloorExample

```java
package airlinetest;

public class FloorExample {

    public static double findFloor(double num) {
        return Math.floor(num);
    }

    public static void main(String[] args) {
        double number = 7.75;
        double floor = findFloor(number);

        System.out.println("Floor of " + number + " is: " + floor);
    }
}
```

### GiftExchange

```java
package airlinetest;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
//There are 5 members A,B,C,D,E. Determine a way such that each gives a gift to other. Provided they cant gift to themselves and pairs can't be repeated. Everytime the result should be different i.e. random order.
public class GiftExchange {

    public static void main(String[] args) {
        String[] members = {"A", "B", "C", "D", "E"};

        List<String> remainingMembers = new ArrayList<>();
        Collections.addAll(remainingMembers, members);

        for (String giver : members) {
            String receiver = getRandomReceiver(giver, remainingMembers);
            remainingMembers.remove(receiver);

            System.out.println(giver + " gives a gift to " + receiver);
        }
    }

    private static String getRandomReceiver(String giver, List<String> remainingMembers) {
        Collections.shuffle(remainingMembers);
        for (String receiver : remainingMembers) {
            if (!giver.equals(receiver)) {
                return receiver;
            }
        }
        // Fallback (should not be reached in this context)
        return remainingMembers.get(0);
    }
}
```

### IndexPairsForSum

```java
package airlinetest;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

//Q2. find out all index pairs in array whose value would sum upto given target
// consider duplicate pairs aslo {1,1,2,3,4,4,5,6,7,8} target=8

public class IndexPairsForSum {

    public static List<int[]> findIndexPairs(int[] nums, int target) {
        List<int[]> result = new ArrayList<>();
        Map<Integer, List<Integer>> numIndices = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            //System.out.println(numIndices.containsKey(complement));
            if (numIndices.containsKey(complement)) {
                List<Integer> indices = numIndices.get(complement);
                for (int index : indices) {
                    result.add(new int[]{index, i});
                }
            }

            // Add the current index to the map
            numIndices.computeIfAbsent(nums[i], k -> new ArrayList<>()).add(i);

            System.out.println(numIndices);
        }

        return result;
    }

    public static void main(String[] args) {
        int[] nums = {1, 1, 2, 3, 4, 4, 5, 6, 7, 8};
        //int[] nums = {0, 1, 2, 3, 4, 5, 6, 7, 8};
        int target = 8;

        List<int[]> indexPairs = findIndexPairs(nums, target);

        System.out.println("Index pairs whose values sum up to " + target + ":");
        for (int[] pair : indexPairs) {
            System.out.println("[" + pair[0] + ", " + pair[1] + "]");
        }
    }
}
```

### LargestElementSmallerThanOrEqualToTarget
package airlinetest;

public class LargestElementSmallerThanOrEqualToTarget {

    public static int findElement(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        int result = -1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] <= target) {
                result = mid;
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        if (result != -1) {
            return nums[result];
        } else {
            // If there is no element smaller than or equal to the target
            return -1; // Or any other value to indicate absence
        }
    }

    public static void main(String[] args) {
        int[] array = {1, 3, 5, 7, 9, 11, 13};
        int target = 6;

        int result = findElement(array, target);

        if (result != -1) {
            System.out.println("Largest element smaller than or equal to " + target + ": " + result);
        } else {
            System.out.println("No element smaller than or equal to " + target + " found.");
        }
    }
}
```

### LightsSwitching

```java
package airlinetest;

public class LightsSwitching {

    public static void main(String[] args) {
        int numLights = 4;
        int numIterations = 6;

        // Array to represent the lights (1 means on, 0 means off)
        int[] lights = new int[numLights];

        for (int iteration = 1; iteration <= numIterations; iteration++) {
            switchLights(lights, iteration % 2 == 1); // Switch on in RBG order for odd iterations

            System.out.println("Iteration " + iteration + ": " + getLightColor(lights));
        }
    }

    private static void switchLights(int[] lights, boolean isRBGOrder) {
        int colorIndex = 0;

        if (!isRBGOrder) {
            // After GR, start with the second color (Green)
            colorIndex = 1;
        }

        for (int i = 0; i < lights.length; i++) {
            lights[i] = 0; // Switch off all lights
        }

        // Switch on one light in the specified color order
        lights[colorIndex] = 1;
    }

    private static String getLightColor(int[] lights) {
        // Get the color of the switched-on light
        for (int i = 0; i < lights.length; i++) {
            if (lights[i] == 1) {
                switch (i) {
                    case 0:
                        return "R";
                    case 1:
                        return "B";
                    case 2:
                        return "G";
                }
            }
        }
        return "Off";
    }
}
```

### MissingNumber

```java
package airlinetest;

public class MissingNumber {

    public static int findMissingNumber(int[] nums) {
        int n = nums.length;
        int xorResult = 0;

        // XOR all elements in the array
        for (int i = 0; i < n; i++) {
            xorResult ^= nums[i];
        }

        // XOR with indices from 0 to n
        for (int i = 0; i <= n; i++) {
            xorResult ^= i;
        }

        return xorResult;
    }

    public static void main(String[] args) {
        int[] array = {3, 0, 1};

        int missingNumber = findMissingNumber(array);

        System.out.println("Missing number in the array: " + missingNumber);
    }
}
```

### MoveNonZerosToEnd

```java
package airlinetest;

import java.util.Arrays;

public class MoveNonZerosToEnd {

    public static void moveNonZerosToEnd(int[] nums) {
        int nonZeroPointer = nums.length - 1;

        // Move non-zero elements to the end
        for (int i = nums.length - 1; i >= 0; i--) {
            if (nums[i] != 0) {
                swap(nums, i, nonZeroPointer);
                nonZeroPointer--;
            }
        }
    }

    private static void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    public static void main(String[] args) {
        int[] array = {0, 2, 0, 4, 1, 0, 3, 0, 5};

        System.out.println("Original Array: " + Arrays.toString(array));

        moveNonZerosToEnd(array);

        System.out.println("Array after moving non-zeros to the end: " + Arrays.toString(array));
    }
}
```

### MoveZeros

```java
package airlinetest;

import java.util.Arrays;

public class MoveZeros {

    public static void moveZeros(int[] nums) {
        int nonZeroPointer = 0;

        // Move non-zero elements to the beginning
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                swap(nums, i, nonZeroPointer);
                nonZeroPointer++;
            }
        }
    }

    private static void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    public static void main(String[] args) {
        int[] array = {0, 2, 0, 4, 1, 0, 3, 0, 5};

        System.out.println("Original Array: " + Arrays.toString(array));

        moveZeros(array);

        System.out.println("Array after moving zeros: " + Arrays.toString(array));
    }
}
```

### NumbersGreaterThanAllToRight

```java
package airlinetest;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class NumbersGreaterThanAllToRight {

    public static List<Integer> findNumbers(int[] nums) {
        List<Integer> result = new ArrayList<>();
        int maxRight = Integer.MIN_VALUE;

        // Iterate from right to left
        for (int i = nums.length - 1; i >= 0; i--) {
            int currentNumber = nums[i];

            // Check if the current number is greater than all numbers to its right
            if (currentNumber > maxRight) {
                result.add(currentNumber);
            }

            // Update the maximum value encountered so far
            maxRight = Math.max(maxRight, currentNumber);
        }

        // Reverse the result list to maintain the original order
        List<Integer> reversedResult = new ArrayList<>();
        for (int i = result.size() - 1; i >= 0; i--) {
            reversedResult.add(result.get(i));
        }

        return reversedResult;
    }

    public static void main(String[] args) {
        int[] array = {4, 6, 3, 2, 8, 10, 7};

        System.out.println("Original Array: " + Arrays.toString(array));

        List<Integer> result = findNumbers(array);

        System.out.println("Numbers greater than all to the right: " + result);
    }
}
```

### PeakIndexInMountainArray
```java
package airlinetest;

public class PeakIndexInMountainArray {

    public static int peakIndexInMountainArray(int[] arr) {
        int left = 0;
        int right = arr.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] < arr[mid + 1]) {
                // We are on the increasing part of the mountain, move to the right
                left = mid + 1;
            } else {
                // We are on the decreasing part of the mountain or at the peak
                // Move to the left, including the current mid (as it could be the peak)
                right = mid;
            }
        }

        // At the end of the loop, left and right point to the peak
        return left;
    }

    public static void main(String[] args) {
        int[] array = {0, 1, 0};

        int peakIndex = peakIndexInMountainArray(array);

        System.out.println("Peak Index in Mountain Array: " + peakIndex);
    }
}
```

### PowerOfTwoChecker

```java
package airlinetest;

public class PowerOfTwoChecker {

    public static boolean isPowerOfTwo(int n) {
        // Check if the integer is positive and has only one set bit
        return n > 0 && (n & (n - 1)) == 0;
    }

    public static void main(String[] args) {
        // Test cases
        System.out.println(isPowerOfTwo(1));   // true
        System.out.println(isPowerOfTwo(16));  // true
        System.out.println(isPowerOfTwo(18));  // false
        System.out.println(isPowerOfTwo(0));   // false
        System.out.println(isPowerOfTwo(-8));  // false
    }
}
```

### RichestCustomerWealth

```java
package airlinetest;

public class RichestCustomerWealth {

    public static int maximumWealth(int[][] accounts) {
        int maxWealth = 0;

        for (int i = 0; i < accounts.length; i++) {
            int currentWealth = 0;
            for (int j = 0; j < accounts[i].length; j++) {
                currentWealth += accounts[i][j];
            }
            maxWealth = Math.max(maxWealth, currentWealth);
        }

        return maxWealth;
    }

    public static void main(String[] args) {
        int[][] accounts = {
            {1, 2, 3},
            {3, 2, 1},
            {4, 5, 6},
            {7, 8, 9}
        };

        int result = maximumWealth(accounts);

        System.out.println("The wealth of the richest customer is: " + result);
    }
}
```

### RotationCountOfArray

```java
package airlinetest;

public class RotationCountOfArray {

    public static int findRotationCount(int[] nums) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {
            if (nums[left] <= nums[right]) {
                // The array is not rotated, the minimum element is at index left
                return left;
            }

            int mid = left + (right - left) / 2;
            int next = (mid + 1) % nums.length;
            int prev = (mid + nums.length - 1) % nums.length;

            if (nums[mid] <= nums[next] && nums[mid] <= nums[prev]) {
                // The minimum element is at index mid
                return mid;
            } else if (nums[mid] <= nums[right]) {
                // The minimum element is in the left half
                right = mid - 1;
            } else if (nums[mid] >= nums[left]) {
                // The minimum element is in the right half
                left = mid + 1;
            }
        }

        return -1; // Not found (should not reach here for a rotated sorted array)
    }

    public static void main(String[] args) {
        int[] array = {4, 5, 6, 7, 0, 1, 2};

        int rotationCount = findRotationCount(array);

        System.out.println("Rotation count of the array: " + rotationCount);
    }
}
```

### SmallestElementGreaterThanOrEqualToTarget

```java
package airlinetest;

public class SmallestElementGreaterThanOrEqualToTarget {

    public static int findElement(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        int result = -1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] >= target) {
                result = mid;
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }

        if (result != -1) {
            return nums[result];
        } else {
            // If there is no element greater than or equal to the target
            return -1; // Or any other value to indicate absence
        }
    }

    public static void main(String[] args) {
        int[] array = {1, 3, 5, 7, 9, 11, 13};
        int target = 6;

        int result = findElement(array, target);

        if (result != -1) {
            System.out.println("Smallest element greater than or equal to " + target + ": " + result);
        } else {
            System.out.println("No element greater than or equal to " + target + " found.");
        }
    }
}
```

### SmallestLetterGreaterThanTarget
```java
package airlinetest;

public class SmallestLetterGreaterThanTarget {

    public static char nextGreatestLetter(char[] letters, char target) {
        int left = 0;
        int right = letters.length;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (letters[mid] <= target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        // If the target is greater than or equal to all letters, wrap around to the first letter
        return letters[left % letters.length];
    }

    public static void main(String[] args) {
        char[] letters = {'c', 'f', 'j'};
        char target = 'a';

        char result = nextGreatestLetter(letters, target);

        System.out.println("Smallest letter greater than " + target + ": " + result);
    }
}
```

### ConvertingCharArrayToListInJava

```java
package Character;

import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class ConvertingCharArrayToListInJava {
    public static void main(String args[]){
        String s = "asdasdasda";
        s.chars().mapToObj(c -> (char) c).collect(Collectors.toList());

        char[] chars = s.toCharArray();
        //      List<Character> list = Arrays.asList(chars); // this does not compile,
        List<char[]> asList = Arrays.asList(chars); // because this DOES compile.
        List<Character> listC = new ArrayList<>();
        for (char c : chars) {
            listC.add(c);
        }
        //And this is how you convert List back to array:
        Character[] array = listC.toArray(new Character[listC.size()]);


        char[] myCharArray = { 'H', 'e', 'l', 'l', 'o', '-', 'X', 'o', 'c', 'e' };

        Stream<Character> myStreamOfCharacters = IntStream
                .range(0, myCharArray.length)
                .mapToObj(i -> myCharArray[i]);

        List<Character> myListOfCharacters = myStreamOfCharacters.collect(Collectors.toList());

        myListOfCharacters.forEach(System.out::println);

        List<Character> list = s.chars().mapToObj( c -> (char)c).collect(Collectors.toList());

        ArrayList<Character> characterList
                = (ArrayList<Character>) s.chars().mapToObj(c -> (char)c).collect(Collectors.toList());

        HashSet<Character> abc =
                (HashSet<Character>) s.chars().mapToObj(c -> (char)c).collect(Collectors.toSet());

        //To get Characters in a specific range from given String
        s.chars().filter(a -> a > 118).mapToObj(c -> (char)c).forEach(a -> System.out.println(a));

        List<Character> characterLst = String.valueOf(chars).chars().mapToObj(i -> (char) i).collect( Collectors.toList() );

        List strList = Stream.of( s.toCharArray() ).map( String::valueOf ).collect( Collectors.toList() );

        List<Character> charlist = String.copyValueOf(myCharArray)
                .chars()
                .mapToObj(i -> (char) i)
                .collect(Collectors.toList());



        StringBuffer st = new StringBuffer("Mike is good");
        System.out.println(replaceWhitespaces(st.toString(), "%20"));
    }

    private static String replaceWhitespaces(String string, String replacement) {
        return string != null ? string.replaceAll("\\s", replacement) : null;


    }
}

```