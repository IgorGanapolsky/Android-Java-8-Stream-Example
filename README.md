# Android Java 8 Stream API Example

Demo app of using Java 8 features with [Retrolambda](https://github.com/orfjackal/retrolambda) and [Lightweight-Stream-API](https://github.com/aNNiMON/Lightweight-Stream-API).

Features:
 - [() -> lambda expression](app/src/main/java/com/annimon/java8streamexample/MainActivity.java#L46);

   ```java
   findViewById(R.id.go).setOnClickListener(v -> {
      final int index = mActionSpinner.getSelectedItemPosition();
      if (index != Spinner.INVALID_POSITION) {
          action(actions[index]);
      }
  });
   ```


 - [Method::references](app/src/main/java/com/annimon/java8streamexample/Word.java#L37);
 
   ```java
   int cmp = Objects.compare(word, other.word, String::compareToIgnoreCase);
   ```


 - [Stream.API()](app/src/main/java/com/annimon/java8streamexample/Utils.java#L38);
 
   ```java
   return Stream.of(lines)
        .map(str -> str.split("\t"))
        .filter(arr -> arr.length == 2)
        .map(arr -> new Word(arr[0], arr[1]))
        .collect(Collectors.toList(new Word[0]));
   ```


 - [switch for "string"](app/src/main/java/com/annimon/java8streamexample/MainActivity.java#L82);
 
   ```java
  switch (action) {
      case "filter 1":
          // Filter one word
          stream = stream.filter(p -> p.getWord().split(" ").length == 1);
          break;
      case "filter 2+":
          // Filter two and more words
          stream = stream.filter(p -> p.getWord().split(" ").length >= 2);
          break;
      // ...
  }
  ```

- [try(with-resources) {}](app/src/main/java/com/annimon/java8streamexample/Utils.java#L27)

  ```java
  final List<String> lines = new LinkedList<>();
  try (final InputStream is = context.getAssets().open("words.txt");
       final InputStreamReader isr = new InputStreamReader(is, "UTF-8");
       final BufferedReader reader = new BufferedReader(isr)) {
      String line;
      while ( (line = reader.readLine()) != null ) {
          lines.add(line);
      }
  } catch (IOException e) {
      Log.e("Java 8 Example", "Utils.readWords", e);
  }
  ```



## Links
  
Demo app: [Java8StreamExample.apk](http://annimon.com/ablogs/file325/Java8StreamExample.apk)

Blog (Russian): [Java 8 в Android со Stream API и лямбдами](http://annimon.com/article/1176)

Retrolambda: https://github.com/orfjackal/retrolambda

Lightweight-Stream-API: https://github.com/aNNiMON/Lightweight-Stream-API



## Screenshots
![screen_1](http://annimon.com/ablogs/file321/stream_api_android_5.png) ![screen_2](http://annimon.com/ablogs/file318/stream_api_android_2.png)