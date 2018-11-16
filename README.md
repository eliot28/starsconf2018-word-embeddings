# Mini-workshop: Representaciones vectoriales de palabras basadas en redes neuronales

Esta página describe los requisitos y los enlaces de descarga para el ["mini-workshop"](https://starsconf2018a.sched.com/event/Hr8L/mini-workshop-representaciones-vectoriales-de-palabras-basadas-en-redes-neuronales) sobre representaciones vectoriales de palabras basadas en redes neuronales que se llevará a cabo en la [Starsconf](https://www.starsconf.com/) 2018.

*En este sitio iremos publicando el material, códigos y referencias respecto al taller.*

**Si asistirás al taller, te recomendamos tener listos los requisitos y descargar los datos que se muestran abajo, ya que en el lugar del evento no habrá conexión a internet.**

## Requisitos

- Python 3.x
- gensim
- numpy
- scikit-learn
- Jupyter Notebook

Una forma sencilla de cumplir con estos requisitos es instalando [Anaconda](https://www.anaconda.com/download/) 
o [Miniconda](https://conda.io/miniconda.html) (Miniconda es mucho más liviano).
Verifica tener el `$PATH` correcto, y luego instala las dependencias usando `conda`:

```
conda install gensim jupyter ipython numpy scikit-learn
```

**Si no tienes Python, puedes usar Colaboratory de Google, accediendo al siguiente notebook y creando una copia en tu cuenta de Google:**

[https://colab.research.google.com/drive/1wMBxQtP_FtGQSXz_mFad5kOndGkZTLl7](https://colab.research.google.com/drive/1wMBxQtP_FtGQSXz_mFad5kOndGkZTLl7)

## Embeddings

Los siguientes son *word embeddings* de palabras en español [1] computados con [fastText](https://github.com/facebookresearch/fastText). Hay tres archivos de distintos tamaños. Para el workshop basta que descargues uno de ellos (dependiendo del espacio que quieras usar y la cantidad de RAM que tengas para poder cargarlos en tu computador después). 

- 100K vectores (94 MB): [http://dcc.uchile.cl/~jperez/word-embeddings/fasttext-sbwc.100k.vec.gz](http://dcc.uchile.cl/~jperez/word-embeddings/fasttext-sbwc.100k.vec.gz) 
- 300K vectores (281 MB): [http://dcc.uchile.cl/~jperez/word-embeddings/fasttext-sbwc.300k.vec.gz](http://dcc.uchile.cl/~jperez/word-embeddings/fasttext-sbwc.300k.vec.gz) 
- 855K vectores (801 MB): [http://dcc.uchile.cl/~jperez/word-embeddings/fasttext-sbwc.vec.gz](http://dcc.uchile.cl/~jperez/word-embeddings/fasttext-sbwc.vec.gz) 

## Probar que todo funcione 👌

Descomprime uno de los archivos, por ejemplo, usando `gzip`:

```
gzip -d fasttext-sbwc.100k.vec.gz
``` 

Ejecuta el siguiente código en python que carga los vectores y lista las diez palabras más similares a la palabra dada:

```
from gensim.models import KeyedVectors
import logging

logging.basicConfig(format='%(asctime)s : %(message)s', level=logging.INFO)

vectors = KeyedVectors.load_word2vec_format('fasttext-sbwc.100k.vec')
print(vectors.most_similar(['adiós']))
```

El output debe verse como lo siguiente:

```
[('despedida', 0.691421627998352), ('despedirse', 0.6398125290870667), ('suspiro', 0.5772554874420166), ('despide', 0.5664263963699341), ('despedirme', 0.5651067495346069), ('querida', 0.5462957620620728), ('beso', 0.5451434850692749), ('llora', 0.5426937937736511), ('despedimos', 0.5414513945579529), ('despidieron', 0.5407767295837402)]
``` 

Si es así, todo bien. Si no, puedes abrir un issue y trataremos de ayudarte.


## Referencias

[1] Word embeddings de palabras en español: [https://github.com/uchile-nlp/spanish-word-embeddings](https://github.com/uchile-nlp/spanish-word-embeddings)
