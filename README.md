<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Piedra, Papel, Tijera</title>
    <script>
        function aleatorio(min, max) {
            return Math.floor(Math.random() * (max - min + 1) + min);
        }

        function eleccion(jugada) {
            let resultado = ""
            if (jugada == 1) {
                resultado = "Piedra 🪨 "
            } else if (jugada == 2) {
                resultado = "Papel 📋 ";
            } else if (jugada == 3) {
                resultado = "Tijera ✂️"
            } else {
                resultado = "Elegiste otro botón, así no se puede jugar 🥹 ahora te tengo que matar 🤪"
            }
            return resultado
        }

        // 1 es piedra, 2 es papel, 3 es tijera
        let triunfos = 0;
        let perdidas = 0;
        let empates = 0;

        function jugar() {
            while (triunfos < 3 && perdidas < 3) {
                const pc = aleatorio(1, 3);
                const jugador = parseInt(prompt("Elige: 1 para piedra, 2 para papel, 3 para tijera"));
                
                // Verificar si el jugador ingresó una opción válida
                if (isNaN(jugador) || jugador < 1 || jugador > 3) {
                    alert("Ingresa una opción válida (1, 2 o 3) o mueres soy mortal con un virus informatico que te matara 😱.");
                    continue; // Vuelve al inicio del bucle sin seguir con el código siguiente
                }

                // Mostrar elección del jugador y de la computadora
                const eleccionPc = eleccion(pc);
                const eleccionJugador = eleccion(jugador);
                alert("Pc elige: " + eleccionPc);
                alert("Tu eliges: " + eleccionJugador);

                // COMBATE
                if (pc === jugador) {
                    alert("EMPATE 🤼");
                    empates = empates + 1; // Incrementar la cantidad de empates
                } else if ((jugador === 1 && pc === 3) || (jugador === 2 && pc === 1) || (jugador === 3 && pc === 2)) {
                    alert("GANASTE 😀");
                    triunfos = triunfos + 1;
                } else {
                    alert("PERDISTE 😒");
                    perdidas = perdidas + 1;
                }
            }

            alert("Ganaste " + triunfos + " veces. Perdiste " + perdidas + " veces. Empataste " + empates + " veces.\n\n¡Felicidades! Has completado el juego con éxito. Se han deducido 100€ de tu cuenta bancaria como tarifa por usar esta versión especial del juego.\n\n¡Gracias por jugar, y por tu dinero, recuerda que la próxima vez solo necesitas tu talento y destreza para vencer!");

            // Preguntar si quiere volver a jugar
            if (confirm("¿Quieres volver a jugar? Ingresa otros 5 euros. Ya con este juego se te cobró del banco cien euros.")) {
                // Si el jugador quiere volver a jugar, reiniciamos las variables y llamamos a la función jugar()
                triunfos = 0;
                perdidas = 0;
                empates = 0;
                jugar();
            }
        }

    </script>
</head>
<body>
    <h1>Piedra, papel o tijera</h1>
    <button onclick="jugar()">Jugar</button>
</body>
</html>
