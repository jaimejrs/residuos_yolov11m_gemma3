# Relatorio de erros — YOLOv11m vs Gemma 3 27B

## Falsos positivos

### YOLOv11m (79 casos)
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
...

### Gemma 3 27B (45 casos)
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
...

## Falsos negativos

### YOLOv11m (85 casos)
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}
- {x}

### Gemma 3 27B (1 casos)
- {x}

## Padroes a verificar por inspecao visual

- FP YOLO: que tipo de cena dispara falso alarme (sombras, texturas de calcada, etc.)
- FP VLM: que tipo de cena confunde o Gemma (vegetacao seca, pavimentos sujos, etc.)
- FN comuns: residuos pequenos, distantes ou ocluidos.

## Nota metodologica
Marca d'agua do Google Street View presente em proporcao equivalente em ambos os grupos,
sem constituir sinal discriminativo entre as classes.

## Vies de rotulo: lixo pequeno nao anotado
O ground truth ignora residuos com area < ~1-2% da imagem (itens muito pequenos
ou ao fundo). O VLM pode identificar esses residuos e retornar `tem_lixo=true`,
sendo contabilizado como falso positivo injustamente. Ao interpretar os FP do VLM,
inspecionar visualmente os casos — alguns podem ser acertos reais nao capturados
pela anotacao. Isso pode indicar que o VLM e mais sensivel a lixo pequeno do que
a convencao de anotacao por regiao permite capturar.
