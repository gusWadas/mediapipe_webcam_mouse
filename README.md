# mediapipe_webcam_mouse
Code using hand landmark tracking with mediapipe to control a mouse with a webcam.

Touchless Screen: WebCam Mouse

Referências
Código base: https://github.com/kinivi/hand-gesture-recognition-mediapipe
pyautogui: https://stackoverflow.com/questions/44294666/command-to-trigger-long-click-on-left-mouse-button

Alterações:
Marca também o polegar
anota posição x e y do dedo indicador

Biblioteca adicionada
import pyautogui

Installs extras necessários:
pip install pyautogui
sudo apt-get install python3-tk python3-dev

Sucesso em guiar o mouse.
Dificuldade em manter posição e abrir mão para clicar
Não consegui verificar se click realmente funcionava
Mouse chacoalha demais

Nova tentativa, usar a posição do dedo mindinho e do polegar em relação ao indicador para clicar. -> Teste primário com a legenda da webcam.

Tentativa de regular o movimento do mouse -> digitalização da posição do mouse (8*(pos//8))

Digitalização da posição funcional, mas ainda chacoalha um pouco. aumentar digitalização para 16.
Distância funciona, mas valor muito baixo para regular clique

Solução -> aumentar multiplicador prévio a tornar int e quadrado de 10 para 100.

Aumento do valor é útil, porém resultado varia de acordo com distância entre a mão e câmera

Solução -> usar y/x ao invés de x^2 + y^2

Solução funcional. Com o polegar estendido, (y+1)/(x+1) <= 10

implementar clique condicional (se posição prévia era menor que 10)

Funciona.
Achar coordenadas para as quais a webcam captura o dedo para fazer um frame de referência

Calcular usando 1000

Valores 750 e 50

Fazer correção de coordenada
hold click não funciona

trocar função click por mouse up e mouse down

Hold-click funcional
Controle da posição ainda imperfeito, mesmo que dentro de patamares desejados
Correção de coordenada funciona, mas não corrige posições para os limites de

Apresentação

Novos goals:
Adicionar função de clique direito e congelar mouse.
Fazer programa secundário com movimento direcionado do mouse
resolver performance (remover detector de gestos)
