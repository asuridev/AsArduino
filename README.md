 <h1 id="inicio">AsArduino</h1>
  <p>AsArduino es un conjunto de librerías que permite resolver de forma asíncrona algunos problemas típicos que surgen
    al momento de programar microcontroladores utilizando el lenguaje de Arduino.
  </p>
  <ul>
    <li><a href="#asled">AsLed</a></li>
    <li><a href="#astime">Astime</a></li>
    <li><a href="#asbutton">AsButton</a></li>
    <li><a href="#asanalogsensor">AsAnalogSensor</a></li>
  </ul>
  <article id="asled">
    <h2>AsLed</h2>
    <p>La librería AsLed permite controlar diodos led de una forma más intuitiva y cómoda, además contiene dos métodos
      asíncronos para generar blink o pulsos.</p>
    <h3>Constructor</h3>
    <code>AsLed NombreLed(pin,tipo_de_activacion);</code>
    <p>
      <b>pin:</b>(byte) Define el número del pin donde se conectará el led. <br>
      <b>tipo de activación:</b>(boolean) Determina el tipo de activación del led, true define activación a nivel alto
      mientras que false es activación a nivel bajo. Opcionalmente podría utlizarse las constantes <b>ACTIVE_HIGH</b> y
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
      <li><b>on():</b> Enciende el led.</li>
      <li><b>off():</b> Apaga el led.</li>
      <li><b>toggle():</b> Cambia el estado del led. </li>
      <li><b>set(boolean):</b> Establece el estado del led según el parámetro boolean que recibe.</li>
      <li><b>brightness(byte):</b> Ajusta el brillo del led segun el parametro recibido (de 0 a 100) funciona solo con
        salidas analógicas.</li>
      <li><b>blink(int):</b> Realiza un efecto estroboscópico(parpadeo) según el tiempo establecido(ms) como parámetro.
      </li>
      <li><b>pulse(byte cantidad, int duracion):</b> Ejecuta un número de encendidos según el primer parámatro, con una
        duración en ms según el segundo parámetro.</li>
      <li><b>start():</b> Inicia la ejecución del método blink() o pulse().</li>
      <li><b>stop():</b> Detiene la ejecución del método blink() o pulse().</li>
    </ul>
    <p>los métodos blink() y pulse() son asíncronos y deben ejecutarse dentro del loop() además su funcionamiento se
      inicia y se detiene con los métodos start() y stop() respectivamente.</p>
  </article>
  <a href="#inicio">Inicio</a>
  <hr>
  
  <article id="astime">
    <h2>AsTime</h2>
    <p>La librería AsTime permite generar temporizadores de una forma asíncrona.</p>
    <h3>Constructor</h3>
    <code>AsTime NombreTimer;</code>
    <br>
    <pre>
        <code>
          #include &lt;AsTime.h&gt;
          AsTime clock1;
        </code>
      </pre>
    <h3>Métodos</h3>
    <ul>
      <li><b>setTimeout(callback, espera):</b> Establece un tiempo de espera de forma asíncrona.
        <ul>
          <li><b>callback:</b>(void Function(void){})funcion que se ejecutará cuando se agote el tiempo de espera</li>
          <li><b>espera:</b>(long) tiempo en milisegundos a esperar.</li>
        </ul>
      </li>
      <li><b>run():</b> Inicia el funcionamiento del método setTimeout.</li>
      <li><b>clear():</b> Detiene el funcionamiento del método setTimeout. </li>
      <li><b>getTime():</b> Retorna (long) el número de ms que han transcurrido desde que se inició un timer (ejecución del método run())</li>
    </ul>
    <p>El método setTimeout es asíncrono y se deberá ejecutar
    dentro del loop() además su funcinamiento inicia y se detiene
    con los métodos run() y clear() respectivamente.</p>
  </article>
  <a href="#inicio">Inicio</a>
  <hr>
  
   <article id="asbutton">
    <h2>AsButton</h2>
    <p>La librería AsButton permite captura los eventos de forma asíncrona de un pulsador. El pulsador debe ser
      normalmente abierto y conectarse a tierra.</p>
    <h3>Constructor</h3>
    <code>AsButton NombrePulsador(pin);</code>
    <p><b>pin:</b>(byte) define el número del pin donde se conectará el pulsador.</p>
    <pre>
          <code>
            #include &lt;AsButton.h&gt;
            AsButton buttonOn(4);
          </code>
        </pre>
    <h3>Métodos</h3>
    <ul>
      <li><b>addEventListener(evento, callback):</b> Establece un tiempo de espera de forma asíncrona.
        <ul>
          <li><b>evento:</b>(String) Parametro que indica el evento a escuchar.
            <ul>
              <li><b>"keydown"</b>evento que se dá una vez se oprime el pulsador.</li>
              <li><b>"keyup"</b>evento que se dá una vez el pulsador es liberado.</li>
              <li><b>"click"</b>evento que se dá cada vez que se oprime y libera rapidamente el pulsador.</li>
              <li><b>"keyhold"</b>evento que se dá cuando se mantine oprimido el pulsador por más de 3 segundos.</li>
            </ul>
          </li>
          <li><b>callback:</b>(void Function(void){})función que se ejecutará una vez se dé el evento configurado</li>
        </ul>
      </li>
    </ul>
    <p>El método addEventListener() es asíncrono y se debe ejecutar dentro del loop().</p>
  </article>
  <a href="#inicio">Inicio</a>
  <hr>
   <article id="asanalogsensor">
    <h2>AsAnalogSensor</h2>
    <p>La librería AsAnalogSensor permite controlar de forma asíncrona los eventos asociados a una entrada analógica.
    </p>
    <h3>Constructor</h3>
    <code>AsAnalogSensor NombreSensor(pin, intervalo,resolucion);</code>
    <p>
      <b>pin:</b> (byte) Define el número del pin de la entrada analógica.<br>
      <b>intervalo:</b>(int) Tiempo en ms en la que se tomaran las muestras.<br>
      <b>resolucion:</b>(float) Número de la resolución del ADC.
    </p>
    <pre>
        <code>
          #include <AsAnalogSensor.h>
          AsAnalogSensor voltimetro(A0, 100, 0.004882);
        </code>
      </pre>
    <h3>Métodos</h3>
    <ul>
      <li><b>addEventListener("evento", delta, callback):</b>sensa los cambios sobre la entrada analógica.
        <ul>
          <li><b>evento:</b>(String) Parámetro que indica el evento a escuchar.
            <ul>
              <li><b>"change"</b>Cambio en el valor de la muestra.</li>
            </ul>
          </li>
          <li><b>delta:</b>(float) Magnitud del cambio de la muestra.</li>
          <li><b>callback:</b>(void Function(float){}) Función que se ejecutará cuando se dé un cambio en la magnitud establecida, recibe como parámetro el valor de la muestra (float)
          </li>
        </ul>
      </li>
    </ul>
  </article>
  <a href="#inicio">Inicio</a>
  <hr>
