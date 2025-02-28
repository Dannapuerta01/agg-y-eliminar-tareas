 <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Agregar y eliminar tareas</title>
    <link rel="stylesheet" type="text/css" href="./style.css">
  </head>
  <body>
    <h1>INTRODUZCA UNA TAREA</h1>
    
    <form onsubmit="return false;">
    <label><span class="text-black">Tarea</span></label>
    <input type="text" id="tareas"><br><br>
     </form>
    
    <button class="btnI">Agregar</button>
    
    <ul id="lista-tareas"></ul>
    <script src="./script.js"></script>
</body>
</html>


body {
  background-color: #000000;
  text-align: center;
  margin: 10px;
}

h1 {
  color: #f774b2;
}

.text-black {
  color: #fdfefe; 
}

input {
  padding: 8px;
  width: 250px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.btnI {  
  color: #000000;
  background-color: #f774b2;
  padding: 15px 35px;
  cursor: pointer;
  border-radius: 5px;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  background: #f8f9fa;
  padding: 10px;
  margin: 5px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button.eliminar {
  background-color: #f774b2;
  color: white;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
}


let inputTareas = document.querySelector("#tareas");
let btnAgregar = document.querySelector(".btnI");
let listatareas= document.querySelector("#lista-tareas");

btnAgregar.addEventListener("click", function() {
    let texto = inputTareas.value.trim(); 

    if (texto === "") {
        alert("Escribe una tarea antes de agregarla :)");
        return;
    }

    let li = document.createElement("li");
    li.textContent = texto;

    let btnEliminar = document.createElement("button");
    btnEliminar.textContent = "X";
    btnEliminar.classList.add("eliminar");

    btnEliminar.addEventListener("click", function() {
        listatareas.removeChild(li);
    });

    li.appendChild(btnEliminar);

    listatareas.appendChild(li);

    inputTareas.value = "";
});

inputTarea.addEventListener("keypress", function(event) {
    if (event.key === "Enter") {
        btnAgregar.click();
    }
});
