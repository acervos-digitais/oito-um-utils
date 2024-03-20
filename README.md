## oito-um-utils

Coleção de notebooks/scripts para ajudar com o processamento de videos.

`rename`: re-nomeia os arquivos de videos para tirar espaços e caracteres especiais.

`resize`: re-dimensiona os videos para 500px e 1152px de largura usando  
`ffmpeg -i input.mp4 -vf scale=500:-2 -an output.mp4`  
`ffmpeg -i input.mp4 -vf scale=1152:-2 -an output.mp4`

`resolution`: extrai informação sobre resolução de todos os videos.

`timestamp`: extrai informacão sobre duração de todos os videos.

---

### metadata

#### `cameras.json`: informação sobre as cameras no formato:

```json
"01-COBERTURA-PP-OESTE": {
  "dir": "01-COBERTURA-PP-OESTE",
  "description": "uma descrição do local",
  "type": "descrição da camera",
  "resolution": [1280, 720],
  "latitude": -15.800873575724609,
  "longitude": -47.86393610757385,
},
```
onde:
- `dir`: nome do diretório com as imagens da camera
- `description`: uma descrição do local
- `type`: descrição da camera
- `resolution`: resolução do video em pixeis
- `latitude`: latitude do local do video
- `longitude`: longitude do local do video


#### `videos.json`: informação sobre os arquivos de vídeo no formato:

```json
"arquivo.mp4" : {
  "name": "arquivo.mp4",
  "camera": "01-COBERTURA-PP-OESTE",
  "length_seconds": 1780,
  "length_frames": 53400,
  "time_start": 1673204400,
  "time_end": 1673206200,
  "continuous": true,
  "seek": [
    [1673204400, 0],
    [1673206200, 1780],
  ],
  "action_score": 0.7,
  "action_seconds": [
    [13, 230],
    [320, 400],
    [917, 45],
  ]
}
```
onde:
- `name`: nome do arquivo de video
- `camera`: id da camera
- `length_seconds`: duração do video em *segundos*
- `length_frames`: duração do video em *frames*
- `time_start`: horário no começo do video (em *unix epoch time*)
- `time_end`: horário no final do video (em *unix epoch time*)
- `continuous`: indica se video é sem cortes (`time_end - time_start == length_seconds`)
- `seek`: lista de pares que mapeiam *unix epoch time* -> posição do vídeo (em *segundos*)
- `action_score`: proporção de frames considerados *importantes*
- `action_frames`: lista de pares que indicam início e duração de sequencias *importantes* (em *segundos*)
