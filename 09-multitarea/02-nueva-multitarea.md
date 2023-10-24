# 2. Nueva multitarea

# 2.1. Clases e interfaces

- En el paquete _java.util.concurrent_ se incluyen nuevas clases e interfaces para la implementación de aplicaciones multitarea
  - clase: Executors
  - interfaces: ExecutorService, Future, Callable

<br>

# 2.2. Interfaz ExecutorService

- Proporciona métodos para el lanzamiento y ejecución de tareas de forma concurrente, utilizando un _pool_ de _threads_

  - _submit(Runnable task)_: lanza la tarea y la pone en ejecución concurrente con el resto
  - _submit(Callable task)_: lo mismo que el anterior, pero para objetos _Callable_
  - _shutdown()_: inicial el final del _pool_ de hilos, por lo que no se aceptarán nuevas tareas

- Se pueden crear implementaciones de _ExecutorService_ a partir de los siguientes métodos estáticos de _Executors_
  - _newCachedThreadPools()_: crea un _ExecutorService_ con un _pool_ de _threads_ variable que se crean a demanda
  - _newFixedThreadPools(int numberThreads)_: crea un _pool_ con un número fijo de _threads_
  - _newSingleThreadExecutor()_: Crea un _ExecutorService_ que utiliza un único _thread_
  - _newScheduledThreadPool(int corePoolSize)_: devuelve un _ScheduledExecutorService_ que permite ejecutar tareas periódicamente

<br>

# 2.3. Interfaz Callable

- Al igual que _Runnable_, implementa una tarea que va a ser ejecutada concurrentemente con otras
- Su único método, _call()_, devuelve un resultado
  - Permite declarar _checked exceptions_
    ```
    public interface Callable<T> {
         T call() throws Exception;
    }
    ```
  - Tarea que calcula la suma de los números del 1 al 100
    ```
    Callable<Integer> callable = () -> {
         int sum = 0;
         for(int i = 1; i <= 100; i++) {
              sum += i;
         }
         return sum;
    }
    ```

<br>

# 2.4. Interfaz Future

- El método _submit(Callable task)_ de _ExecutorService_ devuelve un objeto _Future_ que puede ser utilizado para acceder al resultado de la tarea y controlar su ejecución
- Entre sus métodos están
  - _isDone()_: permite conocer si la tarea ha finalizado
  - _get()_: devuelve el valor generado por _Callable_. Si aún no ha terminado la tarea, queda a la espera del resultado
    ```
    Future<Result_type> t1 = exec.submit(callabeObject);
    while(!t1.isDone()) {
         System.out.println("Wait to end task");
    }
    System.out.println("Result of task": + t1.get());
    ```

<br>

# 2.5. Sincronización

- En las nuevas clases de multitarea la sincronización se lleva a cabo con la interfaz _Lock_ que proporciona los siguientes métodos
  - _void lock()_: bloquea acceso al código a otros hilos
  - _void unlock()_: desbloquea el acceso al código
- Se puede obtener una implementación de _Lock_ instanciando _ReentrantLock_
  ```
  Lock lc = new ReentrantLock();
  lc.lock(); // bloquea el acceso
  lc.unlock(); // desbloquea el acceso
  ```
- Existen otras implementaciones como _ReadLock_ (permite a otros hilos con bloqueo de lectura) o _WriteLock_ (no permite a otros ni lectura ni escritura)

<br>

# 2.6. Colecciones para concurrencia

- El paquete _java.util.concurrent_ incluye interfaces y clases de colección con operaciones _thread safe_:
  - _ConcurrentMap<K,V>_: subinterfaz de _Map_ que garantiza operaciones _thread safe_ en un entorno multitarea. Su principal implementación es _ConcurrentHashMap_
  - _CopyOnWriteArrayList<E>_: variante de _ArrayList_ para entornos _thread safe_
  - _CopyOnWriteArraySet<E>_: variante de _HashSet_ para entornos _thread safe_. Internamente utiliza un _CopyOnWriteArrayList_ para realizar las operaciones
