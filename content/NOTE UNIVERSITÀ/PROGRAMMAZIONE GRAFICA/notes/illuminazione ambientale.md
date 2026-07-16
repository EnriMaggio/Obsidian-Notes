Quando c'è il buio più totale, c'è sempre da qualche parte qualche luce, quindi gli oggetti non sono mai completamente scuri (a percezione).
La luce viene da più fonti sorgente di luce perchè ce ne sono tanti in giro e inoltre anche gli oggetti che riflettono colori sono esso stessi fonti di luce.
Per fare una illuminazione globale si ha bisogno di sofisticati algoritmi

La illuminzazione ambientale risolve questo problema dando del colore ad un oggetto. Semplicemente si usa un fattore di scala detto ambientStrenght per determinare quanto è forte l'illuminazione in caso di scene scure 

```cpp
void main()
{
    float ambientStrength = 0.1;
    vec3 ambient = ambientStrength * lightColor;

    vec3 result = ambient * objectColor;
    FragColor = vec4(result, 1.0);
}  
```

![[Pasted image 20250908112439.png]]