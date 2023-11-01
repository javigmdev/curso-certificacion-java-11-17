# 4. CyclicBarrier

# 4.1. Concepto

- Mecanismo que permite sincronizar la ejecución de un grupo de _threads_
- Objeto que permite que un conjunto de hilos puedan esperarse unos a otros en un determinado punto
- Cuando todos los hilos del grupo alcanzan la barrera, se desbloquean y continúan su ejecución

<br>

# 4.2. Creación

- Se instancian como objetos de la clase _CyclicBarrier_ de _java.util.concurrent_
- Dispone de dos constructores
  - _CyclicBarrier(int threads)_: crea un _CyclicBarrier_ que permite sincronizar el número de hilos indicados en el constructor
  - _CyclicBarrier(int threads, Runnable action)_: cuando todos los hilos alcanzan la barrera, se ejecuta la acción indicada en el segundo parámetro del constructor

<br>

# 4.3. Sincronización de los hilos

- La sincronización de los hilos se realiza a través del método _await()_ de _CyclicBarrier_
- Cuando un hilo llama a este método, queda en espera en ese punto
- Cuando el total de hilos que ha realizado la llamada a _await()_ es igual al valor indicado en el constructor, se liberan todos los hilos y se ejecuta el _Runnable_
- El constructor vuelve a ponerse a 0 tras alcanzar todos los hilos de la barrera

<br>

# 4.4. Ejemplo

- Programa que recupere los números almacenados en tres ficheros distintos y después muestre la suma de los mismos

  ```
  public class Lector implements Runnable {
       CyclicBarrier barrier;
       List<Integer> list;
       String url;

       public Lector(CyclicBarrier barrier, List<Integer> list, String url) {
            super();
            this.barrier = barrier;
            this.list = list;
            this.url = url;
       }

       @Override
       public void run() {
            try {
                 Files.lines(Path.of(url))
                      .forEach(n -> list.add(Integer.parseInt(n)));
                      barrier.await(); // tras la lectura esperan en la barrera
            } catch(IOException | InterruptedException | BrokenBarrierException e) {
                 e.printStackTrace();
            }
       }
  }
  ```

  ```
  public class Lanzador {
       public static void main(String[] args) {
            List<Integer> list = new CopyOnWriteArrayList<>();
            CyclicBarrier barrier = new CyclicBarrier(3, () -> {
                 System.out.prinln(list.stream().mapToInt(n -> n).sum());
            });
            for(int i = 1; i<=3; i++) {
                 new Thread(new Lector(barrier, list, "numbers" + i + ".txt")).start();
            }
       }
  }
  ```
