<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/3.0.1/github-markdown.css"/>
<body class='markdown-body'>
  <section>
    <h1 id='title'>hello, world</h1>
    <figure> timestamp: <time id='time' /></figure>
  </section>
  <section>
    <h1>Color</h1>
    <figure>
      <fieldset id='color'>
	<legend>Hex ~~.> RGB</legend>
	Red: <input id='rgb-red' value='255' maxLength='3'/>
	Green: <input id='rgb-green' value='255' maxLength='3'/>
	Blue: <input id='rgb-blue' value='255' maxLength='3'/>
	<hr/>
	Hex: <code id='rgb-hex'>#ffffff</code>
      </fieldset>
    </figure>
  </section>

  <section>
    <h1>Sha-256</h1>
    <figure>
      <fieldset id='sha-256'>
	<legend><input id='raw' value='42'/></legend>
	Hash: <code id='hash'>73475cb40a568e8da8a045ced110137e159f890ac4da883b6b17dc651b3a8049</code>
      </fieldset>
    </figure>
  </section>
</body>
<script type='text/javascript' src='https://cdnjs.cloudflare.com/ajax/libs/js-sha256/0.9.0/sha256.min.js'></script>
<script>
 ;(function(){
   function dqs(s) { return document.querySelector(s) }
   function si(fn, delay) { setInterval(fn, delay) }

   // init
   ;(function() {
     let d = new Date();
     dqs('#title').innerHTML = `hello, world - <small>${d.getFullYear()} / ${d.getUTCMonth() + 1} / ${d.getUTCDate()} </samll>`;
   })();

   // time
   ;(function(){
     si(() => {
       dqs('#time').innerHTML = Math.floor(new Date().getTime() / 1000);
     }, 1000)
   })();

   // color
   ;(function(){
     const rgb_hex = dqs('#rgb-hex');
     dqs('#color').addEventListener('input', r => {
       rgb_hex.innerHTML = '#'
	 + `${(+ dqs('#rgb-red').value).toString(16)}` 
	 + `${(+ dqs('#rgb-green').value).toString(16)}`
	 + `${(+ dqs('#rgb-blue').value).toString(16)}`

       rgb_hex.style = `background-color: rgba(${dqs('#rgb-red').value}, ${dqs('#rgb-green').value}, ${dqs('#rgb-blue').value})`
     })
   })();

   // sha256
   ;(function() {
     dqs('#sha-256').addEventListener('input', () => {
       dqs('#hash').innerHTML = sha256(dqs('#raw').value);
     })
   })();
   // end
 })(); 
</script>
