## oito-um-utils

Coleção de notebooks/scripts para ajudar com o processamento de videos.

`rename-vids`: re-nomeia os arquivos de videos para tirar espaços e caracteres especiais.

`resize-vids`: re-dimensiona os videos para 500px de largura usando  
`ffmpeg -i input.mp4 -vf scale=500:-2 -an output.mp4`

---

### metadata

`videos.json`: informação sobre os arquivos de vídeo no formato:

```json
"arquivo.mp4" : {
  "name": "arquivo.mp4",
  "dir": "01-COBERTURA-PP-OESTE",
  "length_seconds": 1780,
  "length_frames": 53400,
  "time_start": 1673204400,
  "time_end": 1673206200,
  "latitude": -15.800873575724609,
  "longitude": -47.86393610757385,
  "action_score": 0.7,
  "action_frames": [
    [13, 230],
    [320, 400],
    [9127, 45],
  ]
}
```
onde:
- `name`: nome do arquivo de video
- `dir`: nome do diretório
- `length_seconds`: duração do video em *segundos*
- `length_frames`: duração do video em *frames*
- `time_start`: horário no começo do video (em *unix epoch time*)
- `time_end`: horário no final do video (em *unix epoch time*)
- `latitude`: latitude do local do video
- `longitude`: longitude do local do video
- `action_score`: proporção de frames considerados *importantes*
- `action_frames`: lista de pares que indicam frame inicial e duração de sequencias *importantes*


