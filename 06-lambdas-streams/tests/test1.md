**Question 1**: Which of the following interface definitions can use Lambda expressions?

```
a.
interface A{
}

b.
interface A {
     default void m(){}
}

c.
interface A{
     void m(){}
}

d.
interface A{
     default void m(){}
     void m2();
}

e.
interface A{
     void m1();
     void m2();
}
```

<br>

**Question 2**: Choose the three correct lambda expressions

- a. x->++x
- b. var c->System.out.println(c)
- d. (int a, b)->a+b
- e.()->{return "";}
- f. (@NotNull var x)->x.length()

<br>

**Question 3**: Select a correct implementations of a java.util.function.Function interface (choose 2).

- a. ()->30
- b. (a)->"hello"
- c. (a,b)->System.out.println(a+b)
- d. x->System.out.println(x)
- e. x->x.length()
- f. (a,b)->a.equals(b)

<br>

**Question 4**: Given

```
var nums=List.of(1,2,3,4,5,6);
//line 1
StringBuilder sb=new StringBuilder();
for(int n:nums){
     sb.append(f.apply(n));
     sb.append(" ");
}
System.out.println(sb.toString());
```

Which statement in line 1 enables this code to compile?

- a. Function<Integer, Integer> f=n->n\*2;
- b. Function<Integer> f = n −> n \* 2;
- c. Function<int> f = n −> n \* 2;
- d. Function<int, int> f = n −> n \* 2;
- e. Function f = n −> n \* 2;

<br>

**Question 5**: Which interface in the java.util.function package will return a void return type?:

- a. Supplier
- b. Predicate
- c. Function
- d. Consumer

<br>

**Question 6**: Given:

```
List<String> numbers=Arrays.asList("one","two","three");
Consumer<String> cs=s->System.out.print(s);
Consumer<String> out=cs.andThen(a->System.out.println(":"+a.toUpperCase()));
numbers.forEach(out);
```

Which is the output?

```
a.
     ONE:TWO:THREE
     one:two:three
b.
     one:two:three
     ONE:TWO:THREE
c.
     one:two:three:ONE:TWO:THREE
d.
     one:ONE
     two:TWO
     three:THREE
```

<br>

**Results**:

- **Question 1**: d
- **Question 2**: a, e, f
- **Question 3**: b, e
- **Question 4**: a
- **Question 5**: d
- **Question 6**: d
