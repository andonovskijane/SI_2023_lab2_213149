# Втора лабораториска вежба по Софтверско инженерство
## Јане Андоновски, бр. на индекс 213149
### Control Flow Graph
![cfg Lab2](https://github.com/andonovskijane/SI_2023_lab2_213149/blob/master/Control%20Flow%20Graph.png)

### Цикломатска комплекснот
Цикломатската комплексност може да ја добиеме на два начини: Првиот начин е со броење на регионите во CFG и според тоа излегува дека е 11. Втор начин е со примена на формулата E-N+2, каде E претсавува бројот на ребра (35) и N е бројот на јазли(26). Со замена во формулата добиваме дека цикломатската комплексност е 11.

### Every Branch
Според овој критериум имаме 5 случаеви.

Случај кога user==null.

Случај кога username==null тогаш треба username==email и password.length < 8

Случај кога email нема . или @

Случај кога password нема " " и има special char

Случај кога има " " во password

Користени се следниве тест примери:

- За тест (user=Jane, abc!de,janeandonovski@example.com и непразна листа)
- За тест (username=null, 123 4567, janeandonovski@example.com и непразна листа)
- За тест (Jane, 123456, null и празна листа)
- За тест (Jane, 123 456, janehotmail.com и непразна листа)
- За тест (Jane, 321, jane@hotmail.com и непразна листа)

### Multiple Condition
За овој критериум имаме 4 тест примери:

Тест 1 

        User user1 = null; 
        RuntimeException ex; 
        ex = assertThrows(RuntimeException.class, () -> SILab2.function(user1, users)); 
        assertTrue(ex.getMessage().contains("Mandatory information missing!"));

Тест 2 

        User user2 = new User("Jane", null, "j@gmail.com"); 
        ex = assertThrows(RuntimeException.class, () -> SILab2.function(user2, users)); 
        assertTrue(ex.getMessage().contains("Mandatory information missing!"));

Тест 3 

        User user3 = new User("Jane", "12345", null); 
        ex = assertThrows(RuntimeException.class, () -> SILab2.function(user3, users)); 
        assertTrue(ex.getMessage().contains("Mandatory information missing!"));

Тест 4 

        User user4 = new User("Jane", "J12345$.!", "jane@hotmail.com"); 
        assertTrue(SILab2.function(user4, users));

### Објаснување на напишаните unit tests
- T-X-X -> user==null враќа "true", што значи дека останатите нема потреба да се проверуваат. (условот е исполнет, 1-2)

- F-T-X -> user==null враќа "false", па сега се проверува user.getPassword()==null, што со дадениот тест ќе врати "true", и наредниот израз нема потреба да се проверува. (условот е исполнет, 1-2)

- F-F-T -> user==null и user.getPassword()==null враќаат "false", па сега се проверува user.getEmail()==null, што со дадениот тест ќе врати "true", дополнителни изрази нема за проверување, што значи условот е исполнет. (1-2)

- F-F-F -> доколку сите вратат "false" условот не е исполнет и јазолот 2 се прескокнува. (1-3)
