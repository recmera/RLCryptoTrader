# ¿DDPG o TD3?

DDPG (Deep Deterministic Policy Gradient) es un algoritmo que ha demostrado ser muy efectivo para problemas de control continuo, como el trading. DDPG utiliza redes neuronales profundas para aproximar tanto la función de valor como la política, lo que lo hace especialmente adecuado para problemas con espacios de acción continuos.

<img src="https://spinningup.openai.com/en/latest/_images/math/5811066e89799e65be299ec407846103fcf1f746.svg" width="50%" />

TD3 (Twin Delayed Deep Deterministic Policy Gradient) es una variante de DDPG que ha demostrado ser aún más efectiva en algunos casos. TD3 utiliza dos redes neuronales para aproximar la función de valor, lo que ayuda a reducir la varianza en la estimación de la función de valor.

<img src="https://spinningup.openai.com/en/latest/_images/math/b7dfe8fa3a703b9657dcecb624c4457926e0ce8a.svg" width="50%" />


## Comparativa: 

<table style="border: 1px solid black; border-collapse: collapse;">
    <tr>
        <th style="border: 1px solid black; padding: 5px;">Factor</th>
        <th style="border: 1px solid black; padding: 5px;">DDPG</th>
        <th style="border: 1px solid black; padding: 5px;">TD3</th>
    </tr>
    <tr>
        <td style="border: 1px solid black; padding: 5px;">Número de redes neuronales críticas</td>
        <td style="border: 1px solid black; padding: 5px;">1</td>
        <td style="border: 1px solid black; padding: 5px;">2</td>
    </tr>
    <tr>
        <td style="border: 1px solid black; padding: 5px;">Ruido de exploración</td>
        <td style="border: 1px solid black; padding: 5px;">Ruido Gaussiano aditivo</td>
        <td style="border: 1px solid black; padding: 5px;">Ruido de exploración aditivo</td>
    </tr>
    <tr>
        <td style="border: 1px solid black; padding: 5px;">Uso de objetivos retrasados</td>
        <td style="border: 1px solid black; padding: 5px;">No</td>
        <td style="border: 1px solid black; padding: 5px;">Sí</td>
    </tr>
    <tr>
        <td style="border: 1px solid black; padding: 5px;">Actualización de políticas</td>
        <td style="border: 1px solid black; padding: 5px;">Determinística</td>
        <td style="border: 1px solid black; padding: 5px;">Aleatoria</td>
    </tr>
    <tr>
        <td style="border: 1px solid black; padding: 5px;">Estabilidad del entrenamiento</td>
        <td style="border: 1px solid black; padding: 5px;">Moderada</td>
        <td style="border: 1px solid black; padding: 5px;">Muy alta</td>
    </tr>
    <tr>
        <td style="border: 1px solid black; padding: 5px;">Rendimiento en entornos complejos</td>
        <td style="border: 1px solid black; padding: 5px;">Menos estable</td>
        <td style="border: 1px solid black; padding: 5px;">Más estable</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; padding: 5px;">Tamaño del espacio de acciones</td>
      <td style="border: 1px solid black; padding: 5px;">No es tan efectivo en espacios de acciones grandes debido a su política determinística</td>
      <td style="border: 1px solid black; padding: 5px;">Puede lidiar mejor con la maldición de la dimensionalidad debido al uso de dos redes neuronales críticas y objetivos retrasados</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; padding: 5px;">Tamaño del buffer de experiencia</td>
      <td style="border: 1px solid black; padding: 5px;">No necesita un buffer de experiencia tan grande como TD3 debido a que utiliza una política determinística</td>
      <td style="border: 1px solid black; padding: 5px;">Puede requerir un buffer de experiencia más grande debido al uso de objetivos retrasados y a la naturaleza aleatoria de las actualizaciones de política</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; padding: 5px;">Recompensas escasas</td>
      <td style="border: 1px solid black; padding: 5px;">Puede ser más efectivo en problemas con recompensas escasas debido a su política determinística y la adición de ruido gaussiano aditivo</td>
      <td style="border: 1px solid black; padding: 5px;">Puede ser menos efectivo en problemas con recompensas escasas debido a su uso de objetivos retrasados y la naturaleza aleatoria de las actualizaciones de política</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; padding: 5px;">Complejidad computacional</td>
      <td style="border: 1px solid black; padding: 5px;">Puede ser menos costoso computacionalmente debido a que utiliza una única red neuronal crítica</td>
      <td style="border: 1px solid black; padding: 5px;">Puede ser más costoso computacionalmente debido al uso de dos redes neuronales críticas y objetivos retrasados</td>
    </tr>
</table>