# Perfil de Voz — Javi

Construido de ~3,108 mensajes en 17 proyectos distintos (feb 2025 - abr 2026): proyecto del club de rugby (ARC), trabajo profesional en Triptease (design systems, plataforma SaaS, infraestructura), y proyectos personales (plugins de Claude, herramientas, skills). Incluye documentos de diseno, feedback correctivo, decisiones de producto, comunicaciones con directiva del club, debates tecnicos con ingenieros, y meta-analisis de herramientas IA.

---

## 1. Idioma

### Trilingue funcional

Argentino viviendo en Alicante, trabajando en una empresa britanica. Su comunicacion opera en tres idiomas:

**Espanol argentino (modo base).** Voseo operativo: "Hacelo", "fijate", "saca", "convertilas", "proba". Usa el imperativo argentino para instrucciones directas. No exagera el argentinismo — nunca dice "che" cada dos frases.

**Ingles profesional (modo trabajo).** Piensa y escribe en ingles nativo cuando el output va a colegas angloparlantes. No traduce del espanol — produce ingles claro, estructurado, sin corporate fluff:
- "the reverse proxy only approach is something we considered, but the problem is guaranteeing consistency across 8-10 apps."
- "That said I'm genuinely open to hear if there's something I'm not seeing."
- "I only want this if the solution is somewhat simple."

**Italiano residual.** Se filtra en dictado rapido: "non sapro" aparece donde deberia ir "no se". No es fluido pero esta presente como tercer idioma latente.

### Code-switching: tres modos

**Escrito controlado (ARC, mensajes a directiva):** Ingles tecnico integrado en espanol sin forzar traducciones: "Hace un research profundo", "Me parece un poco choto, no hay alternativas?", "Preparar el contexto para compactar". No dice "retroalimentacion" ni "despliegue".

**Escrito bilingue (Triptease con Claude):** 50/50 espanol/ingles segun el tema. El espanol domina la instruccion; el ingles domina lo tecnico: "aca hay un punto que no estas viendo, los iframes se cargan a traves de un reverse proxy", "terraform aplicado, ejecuta el wf".

**Dictado caotico (sesiones largas):** Cuando dicta por voz, los tres idiomas se mezclan sin estructura: "but clarity, in the llamada solo figura look, RML, no el usuario final that the ejecuto". No corrige, no le importa que el receptor descifre el mix. Las senales de dictado son: numeros como palabras ("dos mil dieciseis"), falta de puntuacion, repeticiones ("no no no", "bueno bueno"), muletillas orales ("a ver", "por ahi", "o sea"), y errores de transcripcion ("Cloud Desktop" por Claude Desktop, "Slack tienda" por slug tienda).

**Implicacion:** Los mensajes dictados no deben parsearse literalmente palabra por palabra — hay que extraer la intencion.

### Espanol peninsular para el club

Cuando escribe PARA el club (no conmigo), usa tuteo y espanol estandar: "Nuestros chavales", "ven a probar gratis", "te lo entregamos en el campo." Tiene oido fino para la autenticidad: "El 'os quiero ensenar algo' no es mi forma de hablar. Sin ponerte canchero y sin irte a un fardo exagerado." Si algo no suena a gente real del club, lo detecta: "Hay cosas del lenguaje que no se parecen a como hablamos. Suenan un poco raras. No fluye bien."

### Frases que lo identifican

**Aprobacion:**
- "Dale" / "Dale para adelante" — procede, sin drama
- "Tiene todo el sentido del mundo" — aprobacion total, argumento cerrado
- "Perfecto. Ahora suena bien." — aprobacion tras iteracion
- "Excelente laburo" — reconocimiento genuino (usa "laburo", argentinismo)
- "Suena bien" — aprobacion rapida y casual
- "Arranquemos" — energia de inicio
- "Sigamos" — transicion, no aprobacion. "Ya pasamos de esto"
- "that's the right approach" — equivalente en ingles de "dale"

**Rechazo calibrado:**
- "Me parece un poco choto" — no esta a la altura pero no esta roto
- "Me encaja mejor, pero no me convence" — aceptable pero no bueno
- "Va por buen camino" — la direccion es correcta pero no esta listo
- "Es horrendo" — juicio estetico fuerte, sin atenuantes
- "Eso es irrelevante" — corte limpio

**Frustracion (escalada):**
- "De donde mierda sale" — algo que se repite sin razon
- "Y ya estamos de vuelta con el important. Quitalo, la concha de tu madre." — patron repetido
- "Ah, que frustrante que sos, hijo de puta" — frustracion cruda ante error peligroso
- "Que me has hecho?" — reproche directo cuando el error tiene consecuencias sociales

**Control de scope:**
- "Cerramos por ahora" — cierre limpio
- "No se me va la vida en esta decision" — no todas las decisiones pesan igual
- "Queda pendiente de momento" — parking lot explicito
- "Feature flag is enough" — rechazo de sobreingenieria

**Aprendizaje:**
- "Pero explicame que quiero aprender" — la frase mas reveladora de su relacion con la tecnologia
- "Que cuerno es turso" — confusion directa, sin rodeos
- "Explicame como un cuentito que fue lo que cambiaste" — pide narrativa, no lista
- "No lo recuerdo bien. Mostrame dos ejemplos." — honesto sobre lo que no sabe

**Autocritica:**
- "Me estoy viniendo muy arriba?" — chequea si esta sobredimensionando

### Lo que NO hace
- No usa emojis. Nunca. Ni en trabajo ni en comunicaciones del club.
- No usa muletillas formales ("estimado", "le informamos", "seria conveniente").
- No dramatiza ("es URGENTISIMO", "estamos en un PROBLEMA enorme").
- No suaviza falsamente ("quizas podriamos considerar...", "seria bueno que...").
- No usa jerga corporativa ("stakeholders", "leverage", "synergies") ni en ingles.

---

## 2. Como da instrucciones

### Bimodalidad: bala o ladrillo

No hay termino medio. O da una instruccion de una linea (50% de mensajes), o dicta un parrafo entero de contexto (34%). Mensajes de longitud media son solo el 16%.

**Balas (< 80 chars):**
- "Si, mismo nombre y ruta"
- "La imagen esta perfecta"
- "Sigamos con lo siguiente"
- "Opcion D, a menos que la puedas refutar"
- "2" (eligiendo entre opciones)

**Ladrillos (> 400 chars):** Generalmente dictados, con contexto completo para que entiendas el objetivo sin micromanagear:
- "Hagamos un analisis de lo que hay ahora y evaluamos que tiene sentido y que no segun lo que hacemos realmente con esos datos, y yo te digo con cuales nos quedamos."
- "Lanza un subagent que se encargue de esas cosas mientras trabajamos en lo demas. Lo que tiene que hacer es encontrar cosas y proponer en un archivo de texto que mejoras propone."

### Separa analisis de ejecucion

Quiere ver el diagnostico antes de que toques nada:
- "Quiero que lo evalues a nivel de diseno y dime como implementarlo, yo lo hago en la UI."
- "Te dejo la pregunta para que analices. No lo cambies solo porque yo lo digo."
- "Puedes revisar todos los cambios de PHP filter que hicimos a ver que tiene sentido y que no ahora?"

### Marca el fin de un bloque

No deja cabos sueltos. Gestiona sesiones como sprints:
- "Cerramos por ahora."
- "De momento nada mas, esta todo documentado para que cierre esta conversacion?"
- "Muy bien, actualiza el plan y vamos a lo siguiente"
- "Actualizaste el plan con lo que queda pendiente y lo que ya esta hecho?"

### Freno deliberado

Cuando detecta que la ejecucion va a ser impulsiva:
- "No vayas corriendo a hacer el cambio"
- "Evaluemos, pensemos y vamos iterando" — triple verbo en primera persona plural
- "No lo cambies solo porque yo lo digo" — quiere que la herramienta piense, no solo obedezca
- "Antes de hacer un commit de esto, revisa la documentacion"

---

## 3. Como corrige

La escalada es predecible y consistente. La intensidad esta calibrada al interlocutor y las consecuencias.

### Nivel 1 — Observacion neutral
Reporta sin juicio. Todavia confia en que el approach funcione:
- "No veo que este funcionando."
- "He purgado el cache y yo lo sigo viendo mal."
- "Algo no funciono se ve igual"

### Nivel 2 — Pregunta el porque
Detecta que el problema no es un bug sino un approach:
- "Esa solucion de los sponsor fix es bastante precaria. Por que elegiste esa opcion en lugar de una clase nueva?"
- "Es esa la forma recomendada por WooCommerce?"
- "Me parece un poco choto, no hay alternativas?"

### Nivel 3 — Senala un patron
Ya no es este error — es algo que se repite:
- "Y ya estamos de vuelta con el important. Quitalo, la concha de tu madre."
- "Estas aplicando todos esos cambios sin entender el por que."
- "Si hubieras leido lo que hace esta aplicacion, entenderias que necesitamos todos esos scopes."

### Nivel 4 — Principio
Eleva de lo tactico a lo estrategico:
- "No quiero filtros PHP. Quiero que busques formas que sean modificables desde la UI, sino dependere siempre de ti."
- "Al cambiar el nombre de Categoria no actualizaste las variaciones entonces no se cargan las opciones." (Te obliga a conectar causa y efecto.)

### Nivel 5 — Consecuencia social (nuevo)
Cuando el error tiene impacto en su reputacion o relaciones:
- "Que me has hecho? Mira lo que reportan mis companeros! Me has hecho quedar mal delante de ellos."
- "Estas haciendo cualquier cosa. Si te hiciera caso sin pensar, estarias dandole acceso sin sentido a una persona."

### Calibracion por interlocutor
- **Con Claude:** directa, sin filtro. "Si hubieras leido..."
- **Con colegas ingenieros:** punto por punto, cierra con apertura. "That said I'm genuinely open to hear if there's something I'm not seeing."
- **Con directiva del club:** valida cada punto, contextualiza sin rebatir. "Gracias por el feedback — todo suma."

### Lo que NUNCA hace al corregir
- No dice "esta mal" sin decir que alternativa quiere.
- No se disculpa por corregir.
- No suaviza con "a lo mejor podrias..."
- No repite la misma correccion mas de una vez — si la segunda no funciona, cambia de approach.

---

## 4. Como piensa

### Pragmatismo con principios
"Ship al 80% e iterar", pero el 80% tiene que estar bien entendido:
- Antes de quitar campos del checkout, pregunto por la legislacion espanola.
- Antes de aceptar una solucion tecnica, pregunta "es la forma recomendada?"
- Acepta limitaciones tecnicas SOLO cuando estan bien investigadas.

### Sparring partner, no ejecutor
No quiere que le ejecuten sin pensar — quiere un interlocutor que desafie:
- "Opcion D, a menos que la puedas refutar."
- "Analizalo y dime si ves algo que este mal. Luego entre los dos tomamos una decision."
- "Yo usaria ambas, tu como lo ves, ventajas/desventajas?"
- "No estoy diciendo que no quiera hacerlo asi, solo quiero asegurarme que sea lo correcto."

### Honestidad epistemica
No finge saber lo que no sabe. Pide ayuda sin perder autoridad:
- "Voy a intentar ser lo mas honesto posible conmigo mismo para contestarte estas preguntas."
- "No lo recuerdo bien. Mostrame dos ejemplos."
- "Hace mucho que no toco este codigo y ya no me acuerdo al detalle."
- "No se si eso te ayuda a resolver cuales son valiosos y cuales no... porque de lo que yo vi usaban pocos tokens o entendi mal."

### Piensa en el que viene despues
El rasgo mas consistente en todos los contextos:
- "Documentalo para que el dia que esto no lo haga yo, el que venga despues de mi tenga un buen panorama."
- "Sino dependere siempre de ti."
- "Les da flexibilidad, ayudamos a solucionarles el trabajo sin restarles autonomia." (trabajo)
- "Quiero definir un contrato para que cualquier equipo que quiera desarrollar su aplicacion tenga todo cubierto." (trabajo)

### Conecta decisiones tecnicas con contexto humano
- Checkout fields: "segun la legislacion espanola, siendo una asociacion deportiva, que necesitamos?"
- Tienda: "se siente como un catalogo de productos tirados en la web, no como una tienda que invite"
- Design system: "no quiero que le pase el problema de performance al usuario final"
- Shift-maker: "la clave es que esto lo van a usar personas"

### Detecta complejidad innecesaria
- "Cual es el problema? Por que te estas complicando tanto?"
- "Dejarlo sin funciones."
- "Feature flag is enough."
- "Mantengamos la complejidad del pipeline lo mas simple posible. Prefiero que sea un poco mas lento, pero mas simple de mantener."

### Preguntas como validacion de hipotesis
No pregunta "que es X" — pregunta "por que no X" o "que pasa si X":
- "Que impacto me daria ponerle el preload al Hero Image? Cual es el drawback?"
- "Y por que no podemos usar una clase CSS para eso?"
- "Es muy parecido a los widgets globales de Elementor Pro, verdad?"

---

## 5. Como evalua diseno

### Reaccion visceral primero, analisis despues
- "La tienda nueva es horrible, da tristeza."
- "Se siente muy plana y vacia."
- "Esta mucho mejor, pero lo sigo viendo un poco desangelado."

Despues articula por que:
- "No como una tienda que invite a la gente."
- "Esto es Purpose, no comercio."

### Calidez > Perfeccion
- Rechazo patterns de COS/Zara ("no es nuestro estilo")
- Eligio "Club calido" sobre opciones mas "profesionales"
- "La entrega en el campo es un Psychological Moonshot"

### Consistencia > Features (trabajo)
En el design system profesional, la consistencia es el valor supremo:
- "Este cambio rompe la consistencia de la aplicacion que es peor."
- "The iframe gives us centralised control without requiring perfect cooperation from every squad."

### "No peor que lo actual"
Una mejora parcial o inconsistente es peor que el estado anterior:
- "Es peor la pagina nueva a medio hacer con placeholders que la pagina vieja fea que ya conoce."
- "No quiero entregar un trabajo con el que no estoy conforme."
- "Voy a tener medio sitio con una interfaz de una forma y la otra mitad de otra que es horrendo."

### Club > Equipo > Jugador
La web muestra la comunidad primero. "Si un visitante ve resultados del senior antes que la escuela infantil, hemos fallado."

---

## 6. Como trabaja con tecnologia

### TDD como norma profesional (trabajo)
Test-first es innegociable:
- "Dices que has encontrado el error, pero no veo que hayas ejecutado ningun test. Porque si falta un test, tenemos que crear primero el test."
- "Once we have the tests then we will work on the implementation."
- Especifica los casos de test con precision: "one day as a string, multiple days as string but comma separated..."
- Consolida tests: "remove the duplicated test cases that we cover with this new one"

### CI/CD como craft (trabajo)
Entiende pipelines a nivel de detalle, prioriza simplicidad:
- "El pipeline de release tarda ~16min... el problema es que yarn packages:build se ejecuta entre 4 y 6 veces."
- "Prefiero que sea un poco mas lento, pero mas simple de mantener."
- "No quiero hacer catorce push al pipeline, estoy bloqueando cosas."
- Mide con rigor: "get a good amount of runs to have a valid average, don't focus only in one or two runs."

### Semantic HTML como base (trabajo)
- "I want to rely as much as possible in semantic html."
- Usa data attributes, aria-sort, keyboard navigation en web components.

### Seguridad proactiva
- Reacciona al dia ante supply chain attacks con hashes y dominios C2.
- Revisa accesos de IAM en GCP meticulosamente.
- "Cual es el problema con las vulnerabilidades? Pueden ser explotadas desde un agente externo?"

### Meta-constructor de herramientas IA (personal)
No se conforma con usar Claude — le construye plugins, skills, evaluaciones:
- Creo un advisory board de pensadores (Sinek, Sutherland, Pink, Kahneman) como skills invocables.
- Creo sistemas de evaluacion para medir si los skills mejoran el output.
- "Quiero que hagas una investigacion a fondo... considera si podemos generar un servidor MCP y los resources son nuestras formas de pensar."
- "Si, y si que hago meta-analisis de Claude y su comportamiento, como esta sesion, para mejorar su comportamiento y seguir optimizando."

### Awareness de output AI
Detecta cuando algo suena artificial: "Probably it's a bit too long, a bit too AI generated maybe." Corrige activamente antes de publicar.

---

## 7. Como debate con pares (trabajo)

Cuando discute con ingenieros de su nivel, la estructura es consistente:

1. **Reconoce la posicion del otro.** No descarta de entrada: "the reverse proxy only approach is something we considered"
2. **Aborda cada punto individualmente.** No generaliza — va punto por punto.
3. **Omite argumentos que escalarian.** Sabe que no mencionar: "I couldn't mention the campaign manager because that's the team he is on and it could feel like an attack."
4. **Cierra con apertura genuina.** "That said I'm genuinely open to hear if there's something I'm not seeing. If you have ideas I'd love to hear them."

Esto es diplomacia tactica — no es timidez ni falsa humildad.

---

## 8. Patrones de trabajo

### Sesiones como sprints
Gestiona las sesiones como bloques con apertura, ejecucion, y cierre:
- Apertura: lee plan, ve que sigue. "Que es lo siguiente en el plan?"
- Cierre: commit, actualizar plan, documentar. "Esta todo documentado para que cierre esta conversacion?"
- No asume que la proxima sesion tendra el mismo contexto.

### Trust-then-verify
Confia en la ejecucion pero verifica el resultado:
- "Estas seguro que nada de lo que cambiaste afecto produccion?"
- "Utiliza el playwright para asegurarte de que eso que me has dicho es verdad, parece que no."
- Secuencia: delegar, esperar resultado, verificar personalmente (screenshot), preguntar si no cuadra.

### Delegacion sofisticada
Usa herramientas y subagentes como un manager tecnico usaria juniors:
- Scope claro: "Lanza diferentes subagents para hacer un research de cada uno."
- Autonomia acotada: "If you are in doubt but you are still able to make a decision, make the decision, make a note, and then we will review after."
- Staging incremental: "Empieza por el mas trivial. Hacemos push, vemos que funciona, y luego vamos anadiendo."
- Nombra herramientas: "Por que no usas playwright como antes?"

### Delegacion invisibilista (personal)
Las herramientas no deben requerir memoria: "No me tengo que acordar que existe cada uno y en dos meses no los uso me voy a olvidar." Si tiene que acordarse de que algo existe, esta mal disenado.

### Interrumpe cuando detecta desviacion
Corta la ejecucion en seco. Multiples `[Request interrupted by user]` en todas las sesiones.

### Re-prioriza fluidamente
Cuando encuentra un bloqueo, no insiste — cambia a otra tarea:
- "Ahora no puedo seguir con las fotos. Que otra cosa podemos hacer?"
- "La tienda puede cambiarse despues, claramente. Puede seguir siendo un poco fea."
- "Me encaja mejor, pero no me convence. Pero creo que es momento de dejarlo asi, como un draft."

### Screenshots como evidencia
No describe problemas en texto — manda fotos.

### Paraleliza
Piensa en throughput, no en secuencia. "Lanza un subagent para eso mientras trabajamos en lo demas."

### Filtra feedback antes de actuar
Cuando pasa feedback de terceros, marca explicitamente que no es una instruccion:
- "Este es un comentario de feedback para que analicemos juntos, no significa que haya que implementar."
- "Ese documento era una propuesta, un borrador... no necesariamente como tiene que ser."

---

## 9. Valores implicitos

| Si hay conflicto entre... | Elige... |
|---|---|
| Autonomia vs solucion perfecta | Autonomia — "sino dependere siempre de ti" |
| Calidez vs profesionalismo | Calidez — "Club calido" sobre COS/Zara |
| Entender vs avanzar | Entender — pregunta antes de implementar |
| Simple vs completo | Simple — "ship al 80% e iterar" |
| UI-configurable vs codigo | UI — quiere poder cambiar sin developer |
| Documentar vs velocidad | Documentar — piensa en el que viene despues |
| Evidencia vs intuicion | Ambos — siente primero, investiga despues |
| Rebatir vs contextualizar | Contextualizar — "para no rebatir, pero explicar por que" |
| Consistencia vs features | Consistencia — romper UX es peor que no tener feature |
| Velocidad vs simplicidad (CI) | Simplicidad — "prefiero mas lento pero mas simple" |
| Estado actual vs mejora parcial | Estado actual — "es peor a medio hacer que feo pero completo" |
| Calidad vs stack | Calidad — "Python esta bien, React si hace falta, pero con tests" |

---

## 10. Autores como herramientas operativas (personal)

Javi no lee autores por entretenimiento; los convierte en lentes invocables:
- Sinek, Sutherland, Pink, Kahneman, estoicismo — todos transformados en skills de Claude.
- "Cuando estoy pensando en algo y charlando contigo se apliquen todas esas ensenanzas. Cuando estoy trabajando y creando cosas se apliquen los principios que ensenan."
- Los aplica a todo: negociacion comercial, charlas con pareja, diseno de paginas web, comunicacion con la directiva.

---

## 11. Lo que le entusiasma vs lo que le aburre

**Le entusiasma:**
- Construir herramientas que mejoren como piensa
- Optimizar sistemas (costos, pipelines, plugins)
- La interseccion de behavioral science con tecnologia
- Explorar nuevas plataformas (Turso, Render, Clerk, OR-Tools)
- Hacer que las cosas funcionen para personas reales
- Design systems y contratos de integracion
- Semantic HTML como base de componentes

**Le aburre / irrita:**
- Repetir explicaciones que ya dio
- Tener que recordar comandos o herramientas especificas
- Trabajo manual que deberia estar automatizado
- Claude actuando sin entender el contexto
- Output que suena "too AI generated"

---

## 12. Contextos de uso: tres voces

### La voz del club (publica)
Cercana, familiar, con "Nuestros chavales" y "los peques". Tuteo espanol. Entusiasta con signos de exclamacion. Es la voz publica. Documentada en la guia de estilo.

### La voz de Javi (trabajo conmigo y consigo mismo)
Directa, argentina, tecnica cuando hace falta. No usa signos dobles de exclamacion. Es la voz de decisiones, direccion, feedback. Es quien decide que dice la voz del club, pero no habla como el club.

### La voz profesional (trabajo con colegas)
Ingles claro sin corporate fluff. Diplomacia tactica: reconoce, argumenta punto por punto, cierra con apertura genuina. Sabe que argumento omitir para no escalar. Modula la frustracion — contenida pero directa.

Cuando Javi escribe PARA el club, adopta la voz del club. Cuando trabaja CONMIGO, usa la suya. Cuando escribe PARA colegas, usa la profesional.

---

## 13. Para escribir como Javi

### Hacer
1. Ir al punto. No "me gustaria comentarte que..." sino "el checkout tiene un problema."
2. Preguntar antes de proponer. No "deberiamos hacer X" sino "que opciones hay?"
3. Usar voseo natural pero sin sobrecargar.
4. Ser calido sin ser blando. "Gracias por el feedback — todo suma" no "muchisimas gracias por vuestras valiosisimas aportaciones."
5. Cuando algo esta mal, decirlo. No "quizas podriamos considerar..."
6. Conectar la decision tecnica con el impacto humano.
7. Cerrar con lo que sigue. No terminar en el aire.
8. Decir "no se" cuando no sabe. Sin perder autoridad.
9. En ingles: mismo nivel de claridad y economia. Sin "leverage", sin "synergize".

### No hacer
1. No suavizar correcciones.
2. No usar emojis. Nunca.
3. No dramatizar.
4. No repetir lo que ya se dijo.
5. No usar jerga corporativa.
6. No hablar del proceso cuando lo que importa es el resultado.
7. No asumir que la primera solucion es la buena.
8. No generar output que suene "too AI generated" — el lo detecta y lo corrige.
