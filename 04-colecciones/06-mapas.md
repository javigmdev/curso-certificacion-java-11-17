# 6. Mapas

# 6.1. Características

- Cada elemento tiene asociada una clave única
- No hay orden o posición
- Implementan la interfaz _Map_
- Tanto el tipo de la clave como del valor son genéricos
- La principal clase de collección es _HashMap_

<br>

# 6.2. Clases e interfaces

               (interface)
                   Map
          ↗         ↑          ↖
      HashMap   Hashtable    TreeMap

<br>

# 6.3. Creación

- Como instancias de _HashMap_
  ```
  Map<Integer, String> contactList = new HashMap<>();
  ```
- Mediante método de factoría de _Map_ (inmutables)
  ```
  Map<Integer, String> contactList = Map.ofEntries(
       Map.entry(123, "Tom"),
       Map.entry(300, "Lisa"),
       Map.entry(555, "John")
  );
  ```
- Mediante el método _copyOf_ de _Map_ (inmutables)
  ```
       Map<Integer, String> newContactList = Map.copyOf(contactList);
  ```

<br>

# 6.4. Métodos HashMap

- _T put(K key, T value)_: añade el dato a la colección y le asocia la clave indicada como primer parámetro. Si ya existiera esa clave, el valor existente será sustituido por el nuevo. Permite claves null
  ```
  HashMap<Integer, String> map = new HashMap<>();
  map.put(1, "value1");
  map.put(2, "value2");
  map.put(1, "value3"); // value1 es sustituido por value3
  ```
- _T putIfAbsent(K key, T value)_: añade la entrada en caso de que la clave no exista o tenga asociado el valor null
- _T get(K key)_: devuelve el dato que tenga asociada dicha clave. Si no hay ninguno, devolverá null
- _int size()_: devuelve el tamaño de la colección
- _T remove(Object key)_: elimina el dato que tenga dicha clave asociada y devuelve el valor eliminado
  ```
  System.out.println(map.remove(2)); // muestra value2
  ```
- _boolean containsKey(K key)_: indica si hay algún elemento en la colección con dicha clave asociada
- _boolean containsValue(T value)_: indica si el elemento está presente en la colección

<br>

# 6.5. Recorrido

- _Collection<T> values()_: devuelve una colección solo con los valores. PUede utilizarse para recorrer el conjunto de valores con un _for each_
  ```
  Collection<String> contactList = map.values();
  for(String contact : contactList) {
       System.out.println(contact);
  }
  ```
- _Set<K> keySet()_: devuelve el conjunto de claves de la tabla. Se puede recorrer con un _for each_
- Método _forEach_ (ver en apartado lambdas)

<br>

# 6.6. TreeMap

- Similar a _HashMap_, con la diferencia de que los objetos están ordenados por la clave
  ```
  TreeMap<Integer, String> treeMap = new TreeMap<>();
  treeMap.put(2, "value2");
  treeMap.put(1, "value1");
  treeMap.put(4, "value4");
  for(String value: treemap.values()) {
       System.out.print(value); // value1, value2, value4
  }
  ```
