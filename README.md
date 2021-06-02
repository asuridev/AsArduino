 <h1 id="inicio">AsArduino</h1>
  <p>AsArduino es un conjunto de librerías que permite resolver de forma asíncrona algunos problemas típicos que surgen
    al momento de programar microcontroladores utilizando el lenguaje de Arduino.
  </p>
  <ul>
    <li><a href="#asled">AsLed</a></li>
    <li><a href="#astime">Astime</a></li>
    <li><a href="#">AsButton</a></li>
    <li><a href="#">AsAnalogSensor</a></li>
  </ul>
  <article id="asled">
    <h2>AsLed</h2>
    <p>la librería AsLed permite controlar diodos led de una forma más intuitiva y cómoda. además contiene dos métodos
      asíncronos para generar blink o pulsos.</p>
    <h3>Constructor</h3>
    <code>AsLed NombreLed(pin,tipo_de_activacion);</code>
    <p>
      <b>pin:</b>(byte) define el número del pin donde se conectará el led <br>
      <b>tipo de activación:</b>(boolean) determina el tipo de activación del led, true define activación a nivel alto
      mientras que false es activación a nivel bajo. opcionalmente podría utlizarse las constantes <b>ACTIVE_HIGH</b> y
      <b>ACTIVE_LOW</b> para definir el tipo de activación.
    </p>
    <pre>
      <code>
        #include &lt;AsLed.h&gt;
        AsLed ledEstado(13,ACTIVE_HIGH);
      </code>
    </pre>
    <h3>Métodos</h3>
    <ul>
      <li><b>on():</b> Enciende el led</li>
      <li><b>off():</b> Apaga el led</li>
      <li><b>toggle():</b> Cambia el estado del led </li>
      <li><b>set(boolean):</b> Establece el estado del led según el parámetro boolean que recibe.</li>
      <li><b>brightness(byte):</b> Ajusta el brillo del led segun el parametro recibido (de 0 a 100) funciona solo con
        salidas analógicas</li>
      <li><b>blink(int):</b> Realiza un efecto estroboscópico(parpadeo) según el tiempo establecido(ms) como parametro
      </li>
      <li><b>pulse(byte cantidad, int duracion):</b> Ejecuta un número de encendidos según el primer paramatro, con una
        duración en ms según el segundo parámetro</li>
      <li><b>start():</b> Inicia la ejecución del método blink() o pulse()</li>
      <li><b>stop():</b> Detiene la ejecución del método blink() o pulse()</li>
    </ul>
    <p>los metodos blink() y pulse() son asíncronos y deben ejecutarse dentro del loop() además su funcionamiento se
      inicia y se detiene con los métodos start() y stop() respectivamente</p>
  </article>
  <a href="#inicio">Inicio</a>
  <hr>
  
  <article id="astime">
    <h2>AsTime</h2>
    <p>La librería AsTime permite generar temporizadores de una forma asíncrona</p>
    <h3>Constructor</h3>
    <code>AsTime NombreTimer;</code>
    <pre>
        <code>
          #include &lt;AsTime.h&gt;
          AsTime clock1;
        </code>
      </pre>
    <h3>Métodos</h3>
    <ul>
      <li><b>setTimeout(callback, espera):</b> Establece un tiempo de espera de forma asíncrona
        <ul>
          <li><b>callback:</b>(void Function(void){})funcion que se ejecutará cuando se agote el tiempo de espera</li>
          <li><b>espera:</b>(long) tiempo en milisegundos a esperar</li>
        </ul>
      </li>
      <li><b>run():</b> Inicia el funcionamiento del método setTimeout</li>
      <li><b>clear():</b> Detiene el funcionamiento del método setTimeout </li>
      <li><b>getTime():</b> Retorna (long) el numero de ms que han transcurrido desde que se inicio un timer (ejecucion del metodo run())</li>
    </ul>
    <p>El metodo setTimeout es asíncrono y se deberá ejecutar
    dentro del loop() ademas su funcinamiento inicia y se detiene
    con los metodos run() y clear() respectivamente</p>
  </article>
  <a href="#inicio">Inicio</a>
  <hr>
