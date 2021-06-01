 <h1>AsArduino</h1>
  <p>AsArduino es un conjunto de librerías que permite resolver de forma asíncrona algunos problemas típicos que surgen
    al momento de programar microcontroladores utilizando el lenguaje de Arduino.
  </p>
  <ul>
    <li><a href="#asled">AsLed</a></li>
    <li><a href="#">Astime</a></li>
    <li><a href="#">AsButton</a></li>
    <li><a href="#">AsAnalogSensor</a></li>
  </ul>
  <article id="asled">
    <h2>AsLed</h2>
    <p>la libreria AsLed permite controlar diodos led de una forma mas intuitiva y comoda. ademas contiene dos metodos
      asincronos para generar blink o pulsos.</p>
    <h3>Constructor</h3>
    <code>AsLed NombreLed(pin,tipo_de_activacion);</code>
    <p>
      <b>pin:</b>(byte) define el pin donde se conectará el led <br>
      <b>tipo de activacion:</b>(boolean) determina el tipo de activacion del led, true define activacion a nivel alto
      mientras que false activacion a nivel bajo. opcionalmente podria utlizarze las constantes <b>ACTIVE_HIGH</b> y
      <b>ACTIVE_LOW</b> para definir el tipo de activacion.
    </p>
    <code>
      <pre>
          #include AsLed.h
          AsLed ledEstado(13,ACTIVE_HIGH);
      </pre>
    </code>
  </article>
