---
title: "¿Qué es la Codificación en Base64?"
category: Informática
tags: Informática
date: 2023-04-09 02:00
published: true
page_id: 24
---

<div id="Base64"></div>
## ¿Qué es la Codificación en Base64?

La codificación en **Base64** es un sistema de numeración posicional que usa 64 como base. Es la mayor potencia que puede ser representada usando únicamente los caracteres imprimibles de **ASCII**. Podemos ver a *Base64* como un grupo de esquemas de codificación de binario a texto que representa los datos binarios mediante una cadena *ASCII*.

Todas las variantes famosas que se conocen con el nombre de *Base64* usan el rango de caracteres **A-Z**, **a-z** y **0-9** en este orden para los primeros 62 dígitos, pero los símbolos escogidos para los últimos dos dígitos varían considerablemente de unas a otras, normalmente, siendo los símbolos *'='* y *'+'* como símbolos extras.

Para fines prácticos veremos un ejemplo con el título del libro de <a href="/Software Libre/Quien-es-Richard-Stallman">Richard Matthew Stallman</a> Fundador del <a href="/Software Libre/Que-es-la-Free-Software-Fundation-(FSF)">Movimiento del Software Libre</a>: *'Free as in Freedom: Richard Stallman's Crusade for Free Software'*

Tomando las palabras **“Free as in Freedom”** quedaría codificado en Base64 como:

    RnJlZSBhcyBpbiBGcmVlZG9t

En las palabras anteriores los 3 primeros caracteres, **'Fre'**, codificado es **'RnJl'**. Codificado en **ASCII** *F*, *r* y *e* son almacenadas como los bytes *70*, *114* y *101*, es decir, *01000110*, *01110010* y *01100101* en **base 2**.

Ahora esos tres *bytes* se unen y tenemos el búfer de *24 bits*, que será *010001100111001001100101*. Este número se convertirá a su valor *Base64*, que puede hacerse tomando bloques de *6 bits* a la vez (*6 bits* forman como máximo *64* valores diferentes en binario: **2**<sup>**6**</sup>). A continuación, tomando cada vez *6 bits del búfer*, tenemos 4 números *(24 = 6 x 4)*, que entonces son convertidos a su correspondiente valor en *Base64*.

<table class="dark">
    <thead>
        <tr>
            <th class="dark-title">Texto de entrada</th>
            <th colspan=8>F</th>
            <th colspan=8>r</th>
            <th colspan=8>E</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="dark-title">ASCII</td>
            <td colspan=8>70</td>
            <td colspan=8>114</td>
            <td colspan=8>101</td>
        </tr>
        <tr>
            <td class="dark-title">Bits</td>
            <td>0</td><td>1</td><td>0</td><td>0</td>
            <td>0</td><td>1</td><td>1</td><td>0</td>
            <td>0</td><td>1</td><td>1</td><td>1</td>
            <td>0</td><td>0</td><td>1</td><td>0</td>
            <td>0</td><td>1</td><td>1</td><td>0</td>
            <td>0</td><td>1</td><td>0</td><td>1</td>
        </tr>
        <tr>
            <td class="dark-title">Índice</td>
            <td colspan=6>17</td>
            <td colspan=6>39</td>
            <td colspan=6>9</td>
            <td colspan=6>37</td>
        </tr>
        <tr>
            <td class="dark-title">Resultado en Base64</td>
            <td colspan=6>R</td>
            <td colspan=6>n</td>
            <td colspan=6>J</td>
            <td colspan=6>l</td>
        </tr>
    </tbody>
</table>

Por tanto, 3 bytes sin codificar (en este caso, caracteres ASCII) entran y 4 caracteres ASCII codificados surgen como resultado.

<div id="Tabla"><br></div>
## Tabla de índice Base64

<table class="dark">
    <thead>
        <tr class="dark-title">
            <th>Valor</th><th>Carácter</th>
            <th>Valor</th><th>Carácter</th>
            <th>Valor</th><th>Carácter</th>
            <th>Valor</th><th>Carácter</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0</td><td>A</td>
            <td>16</td><td>Q</td>
            <td>32</td><td>g</td>
            <td>48</td><td>w</td>
        </tr>
        <tr>
            <td>1</td><td>B</td>
            <td>17</td><td>R</td>
            <td>33</td><td>h</td>
            <td>49</td><td>x</td>
        </tr>
        <tr>
            <td>2</td><td>C</td>
            <td>18</td><td>S</td>
            <td>34</td><td>i</td>
            <td>50</td><td>y</td>
        </tr>
        <tr>
            <td>3</td><td>D</td>
            <td>19</td><td>T</td>
            <td>35</td><td>j</td>
            <td>51</td><td>z</td>
        </tr>
        <tr>
            <td>4</td><td>E</td>
            <td>20</td><td>U</td>
            <td>36</td><td>k</td>
            <td>52</td><td>0</td>
        </tr>
        <tr>
            <td>5</td><td>F</td>
            <td>21</td><td>V</td>
            <td>37</td><td>l</td>
            <td>53</td><td>1</td>
        </tr>
        <tr>
            <td>6</td><td>G</td>
            <td>22</td><td>W</td>
            <td>38</td><td>m</td>
            <td>54</td><td>2</td>
        </tr>
        <tr>
            <td>7</td><td>H</td>
            <td>23</td><td>X</td>
            <td>39</td><td>n</td>
            <td>55</td><td>3</td>
        </tr>
        <tr>
            <td>8</td><td>I</td>
            <td>24</td><td>Y</td>
            <td>40</td><td>o</td>
            <td>56</td><td>4</td>
        </tr>
        <tr>
            <td>9</td><td>J</td>
            <td>25</td><td>Z</td>
            <td>41</td><td>p</td>
            <td>57</td><td>5</td>
        </tr>
        <tr>
            <td>10</td><td>K</td>
            <td>26</td><td>a</td>
            <td>42</td><td>q</td>
            <td>58</td><td>6</td>
        </tr>
        <tr>
            <td>11</td><td>L</td>
            <td>27</td><td>b</td>
            <td>43</td><td>r</td>
            <td>59</td><td>7</td>
        </tr>
        <tr>
            <td>12</td><td>M</td>
            <td>28</td><td>c</td>
            <td>44</td><td>s</td>
            <td>60</td><td>8</td>
        </tr>
        <tr>
            <td>13</td><td>N</td>
            <td>29</td><td>d</td>
            <td>45</td><td>t</td>
            <td>61</td><td>9</td>
        </tr>
        <tr>
            <td>14</td><td>O</td>
            <td>30</td><td>e</td>
            <td>46</td><td>u</td>
            <td>62</td><td>+</td>
        </tr>
        <tr>
            <td>15</td><td>P</td>
            <td>31</td><td>f</td>
            <td>47</td><td>v</td>
            <td>63</td><td>=</td>
        </tr>
    </tbody>
</table>
