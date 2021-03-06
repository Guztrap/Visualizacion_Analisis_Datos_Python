## ¡Bienvenido a tu primer proyecto de datos!

Echa un vistazo al Kaggle Titanic Challenge en el siguiente enlace:

https://www.kaggle.com/c/titanic-gettingStarted

Nota: Deberá crear una cuenta para acceder a los datos.

Descargue el archivo train.csv y guárdelo en la misma ubicación que sus Notebooks.


```python
# Ahora vamos a abrirlo con pandas
import pandas as pd
from pandas import Series,DataFrame

# Configure el archivo csv Titanic como un DataFrame
titanic_df = pd.read_csv('../data/Titanic_train.csv')

# Veamos una vista previa de los datos
titanic_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# También podríamos obtener información general para el conjunto de datos
titanic_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 12 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   PassengerId  891 non-null    int64  
     1   Survived     891 non-null    int64  
     2   Pclass       891 non-null    int64  
     3   Name         891 non-null    object 
     4   Sex          891 non-null    object 
     5   Age          714 non-null    float64
     6   SibSp        891 non-null    int64  
     7   Parch        891 non-null    int64  
     8   Ticket       891 non-null    object 
     9   Fare         891 non-null    float64
     10  Cabin        204 non-null    object 
     11  Embarked     889 non-null    object 
    dtypes: float64(2), int64(5), object(5)
    memory usage: 83.7+ KB
    


```python
print(titanic_df.columns.values)
```

    ['PassengerId' 'Survived' 'Pclass' 'Name' 'Sex' 'Age' 'SibSp' 'Parch'
     'Ticket' 'Fare' 'Cabin' 'Embarked' 'person' 'Alone' 'Survivor']
    


```python
titanic_df.describe(include=['O'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Sex</th>
      <th>Ticket</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
      <th>Alone</th>
      <th>Survivor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>891</td>
      <td>891</td>
      <td>891</td>
      <td>204</td>
      <td>889</td>
      <td>891</td>
      <td>891</td>
      <td>891</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>891</td>
      <td>2</td>
      <td>681</td>
      <td>147</td>
      <td>3</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Rood, Mr. Hugh Roscoe</td>
      <td>male</td>
      <td>CA. 2343</td>
      <td>B96 B98</td>
      <td>S</td>
      <td>male</td>
      <td>Alone</td>
      <td>no</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>1</td>
      <td>577</td>
      <td>7</td>
      <td>4</td>
      <td>644</td>
      <td>537</td>
      <td>537</td>
      <td>549</td>
    </tr>
  </tbody>
</table>
</div>



Todos los buenos proyectos de análisis de datos comienzan tratando de responder preguntas. Ahora que sabemos qué datos de categoría de columna tenemos, pensemos en algunas preguntas o ideas que nos gustaría obtener de los datos. ¡Aquí hay una lista de preguntas que intentaremos responder usando nuestras nuevas habilidades de análisis de datos!

Primero algunas preguntas básicas:

    1.) ¿Quiénes eran los pasajeros en el Titanic? (Edades, género, clase, etc.)
    2.) ¿En qué cubierta estaban los pasajeros y cómo se relaciona eso con su clase?
    3.) ¿De dónde vinieron los pasajeros?
    4.) ¿Quién estaba solo y quién estaba con la familia?
    
Luego profundizaremos, con una pregunta más amplia:

    5.) ¿Qué factores ayudaron a alguien a sobrevivir al hundimiento?

Entonces, comencemos con la primera pregunta: ¿Quiénes fueron los pasajeros del Titanic?


```python
# Vamos a importar lo que necesitaremos para el análisis y la visualización.
# Importemos las librerias que vamos a utilizar
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```


```python
# Primero verifiquemos el género
#sns.factorplot('Sex',data=titanic_df)
sns.catplot('Sex',data=titanic_df,kind="count")
```




    <seaborn.axisgrid.FacetGrid at 0x202688fb9b0>




![png](/images/titanic/output_8_1.png)



```python
# Ahora separemos los géneros por clases, ¡recuerden que podemos usar el argumento 'hue' aquí!
#sns.catplot('Pclass',hue='Sex',data=titanic_df)
sns.catplot('Pclass',hue='Sex',data=titanic_df,kind="count")
```




    <seaborn.axisgrid.FacetGrid at 0x2026890dd30>




![png](/images/titanic/output_9_1.png)


Wow, un buen número de hombres más en la tercera clase que las mujeres, un hallazgo interesante. Sin embargo, podría ser útil saber la división entre hombres, mujeres y niños. ¿Cómo podemos hacer esto?


```python
# Trataremos a cualquier persona menor de 16 años como un niño, y luego usaremos la técnica de aplicar una función para crear una nueva columna
# Primero hagamos una función para clasificar el sexo
def male_female_child(passenger):
    # Tome la edad y el sexo
    age,sex = passenger
    # Compara la edad, de lo contrario deja el sexo
    if age < 16:
        return 'child'
    else:
        return sex
# Definiremos una nueva columna llamada 'persona', recuerde especificar axis = 1 para columnas y no indexar
titanic_df['person'] = titanic_df[['Age','Sex']].apply(male_female_child,axis=1)
```


```python
# Let's see if this worked, check out the first ten rows
titanic_df[0:10]
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;">
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>  1</td>
      <td> 0</td>
      <td> 3</td>
      <td>                           Braund, Mr. Owen Harris</td>
      <td>   male</td>
      <td> 22</td>
      <td> 1</td>
      <td> 0</td>
      <td>        A/5 21171</td>
      <td>  7.2500</td>
      <td>  NaN</td>
      <td> S</td>
      <td>   male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>  2</td>
      <td> 1</td>
      <td> 1</td>
      <td> Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td> female</td>
      <td> 38</td>
      <td> 1</td>
      <td> 0</td>
      <td>         PC 17599</td>
      <td> 71.2833</td>
      <td>  C85</td>
      <td> C</td>
      <td> female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>  3</td>
      <td> 1</td>
      <td> 3</td>
      <td>                            Heikkinen, Miss. Laina</td>
      <td> female</td>
      <td> 26</td>
      <td> 0</td>
      <td> 0</td>
      <td> STON/O2. 3101282</td>
      <td>  7.9250</td>
      <td>  NaN</td>
      <td> S</td>
      <td> female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>  4</td>
      <td> 1</td>
      <td> 1</td>
      <td>      Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td> female</td>
      <td> 35</td>
      <td> 1</td>
      <td> 0</td>
      <td>           113803</td>
      <td> 53.1000</td>
      <td> C123</td>
      <td> S</td>
      <td> female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>  5</td>
      <td> 0</td>
      <td> 3</td>
      <td>                          Allen, Mr. William Henry</td>
      <td>   male</td>
      <td> 35</td>
      <td> 0</td>
      <td> 0</td>
      <td>           373450</td>
      <td>  8.0500</td>
      <td>  NaN</td>
      <td> S</td>
      <td>   male</td>
    </tr>
    <tr>
      <th>5</th>
      <td>  6</td>
      <td> 0</td>
      <td> 3</td>
      <td>                                  Moran, Mr. James</td>
      <td>   male</td>
      <td>NaN</td>
      <td> 0</td>
      <td> 0</td>
      <td>           330877</td>
      <td>  8.4583</td>
      <td>  NaN</td>
      <td> Q</td>
      <td>   male</td>
    </tr>
    <tr>
      <th>6</th>
      <td>  7</td>
      <td> 0</td>
      <td> 1</td>
      <td>                           McCarthy, Mr. Timothy J</td>
      <td>   male</td>
      <td> 54</td>
      <td> 0</td>
      <td> 0</td>
      <td>            17463</td>
      <td> 51.8625</td>
      <td>  E46</td>
      <td> S</td>
      <td>   male</td>
    </tr>
    <tr>
      <th>7</th>
      <td>  8</td>
      <td> 0</td>
      <td> 3</td>
      <td>                    Palsson, Master. Gosta Leonard</td>
      <td>   male</td>
      <td>  2</td>
      <td> 3</td>
      <td> 1</td>
      <td>           349909</td>
      <td> 21.0750</td>
      <td>  NaN</td>
      <td> S</td>
      <td>  child</td>
    </tr>
    <tr>
      <th>8</th>
      <td>  9</td>
      <td> 1</td>
      <td> 3</td>
      <td> Johnson, Mrs. Oscar W (Elisabeth Vilhelmina Berg)</td>
      <td> female</td>
      <td> 27</td>
      <td> 0</td>
      <td> 2</td>
      <td>           347742</td>
      <td> 11.1333</td>
      <td>  NaN</td>
      <td> S</td>
      <td> female</td>
    </tr>
    <tr>
      <th>9</th>
      <td> 10</td>
      <td> 1</td>
      <td> 2</td>
      <td>               Nasser, Mrs. Nicholas (Adele Achem)</td>
      <td> female</td>
      <td> 14</td>
      <td> 1</td>
      <td> 0</td>
      <td>           237736</td>
      <td> 30.0708</td>
      <td>  NaN</td>
      <td> C</td>
      <td>  child</td>
    </tr>
  </tbody>
</table>
</div>



Excellent! Now we have seperated the passengers between female,male,and child. This will be important later on beacuse of the famous "Women and children first policy"!


```python
# ¡Intentemos el catplot nuevamente!
#sns.catplot('Pclass',data=titanic_df,hue='person')
sns.catplot('Pclass',hue='person',data=titanic_df,kind="count")
```




    <seaborn.axisgrid.FacetGrid at 0x20268a91eb8>




![png](/images/titanic/output_14_1.png)


¡Interesante, bastantes niños en 3ra clase y no tantos en 1ra! ¿Qué tal si creamos una distribución de las edades para obtener una imagen más precisa de quiénes eran los pasajeros?


```python
# Forma rápida de crear un histograma usando pandas
titanic_df['Age'].hist(bins=70)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x2026a010588>




![png](/images/titanic/output_16_1.png)



```python
# También podríamos obtener una comparación general rápida de hombres, mujeres y niños.
titanic_df['person'].value_counts()
```




    male      537
    female    271
    child      83
    Name: person, dtype: int64




```python
# Otra forma de visualizar los datos es usar FacetGrid para trazar múltiples kedplots en un solo diagrama
# Establezca la figura igual a una cuadrícula de facetas con el marco de datos de pandas como fuente de datos, 
# establezca el tono y cambie la relación de aspecto.
fig = sns.FacetGrid(titanic_df, hue="Sex",aspect=4)

# Luego use el mapa para trazar todos los kdeplots posibles para la columna 'Edad' por la elección del tono
fig.map(sns.kdeplot,'Age',shade= True)

# Establecer el límite máximo x por la pasajera más vieja.
oldest = titanic_df['Age'].max()
oldest

# Como sabemos que nadie puede tener años negativos, establezca el límite inferior x en 0
fig.set(xlim=(0,oldest))

# Como sabemos que nadie puede tener años negativos, establezca el límite inferior x en 0
fig.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x2026b395898>




![png](/images/titanic/output_18_1.png)



```python
# Podríamos haber hecho lo mismo para que la columna 'persona' incluya niños
fig = sns.FacetGrid(titanic_df, hue="person",aspect=4)
fig.map(sns.kdeplot,'Age',shade= True)
oldest = titanic_df['Age'].max()
fig.set(xlim=(0,oldest))
fig.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x2026b339668>




![png](/images/titanic/output_19_1.png)



```python
# Hagamos lo mismo para la clase cambiando el argumento hue:
fig = sns.FacetGrid(titanic_df, hue="Pclass",aspect=4)
fig.map(sns.kdeplot,'Age',shade= True)
oldest = titanic_df['Age'].max()
fig.set(xlim=(0,oldest))
fig.add_legend()

```




    <seaborn.axisgrid.FacetGrid at 0x2026b0c8588>




![png](/images/titanic/output_20_1.png)


Nos hemos hecho una buena idea de quiénes eran los pasajeros según sexo, edad y clase. Entonces pasemos a nuestra segunda pregunta: ¿En qué cubierta estaban los pasajeros y cómo se relaciona eso con su clase?


```python
# Veamos nuevamente nuestro conjunto de datos
titanic_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
  </tbody>
</table>
</div>




```python
titanic_df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>714.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>446.000000</td>
      <td>0.383838</td>
      <td>2.308642</td>
      <td>29.699118</td>
      <td>0.523008</td>
      <td>0.381594</td>
      <td>32.204208</td>
    </tr>
    <tr>
      <th>std</th>
      <td>257.353842</td>
      <td>0.486592</td>
      <td>0.836071</td>
      <td>14.526497</td>
      <td>1.102743</td>
      <td>0.806057</td>
      <td>49.693429</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.420000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>223.500000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>20.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>7.910400</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>446.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>14.454200</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>668.500000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>38.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>31.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>891.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>80.000000</td>
      <td>8.000000</td>
      <td>6.000000</td>
      <td>512.329200</td>
    </tr>
  </tbody>
</table>
</div>



Entonces podemos ver que la columna Cabina tiene información sobre el mazo, pero tiene varios valores de NaN, por lo que tendremos que descartarlos.


```python
# Primero, borraremos los valores de NaN y crearemos un nuevo objeto, mazoFirst we'll drop the NaN values and create a new object, deck
deck = titanic_df['Cabin'].dropna()
```


```python
# Un preview de los datos
deck.head()
```




    1      C85
    3     C123
    6      E46
    10      G6
    11    C103
    Name: Cabin, dtype: object



Tenga en cuenta que solo necesitamos la primera letra del mazo para clasificar su nivel (por ejemplo, A, B, C, D, E, F, G)


```python

# Así que tomemos esa letra para el nivel de deck con un bucle

# Establecer lista vacía
levels = []

# Bucle para tomar la primera letra
for level in deck:
    levels.append(level[0])    

# Restablecer DataFrame y usar el gráfico de factores
cabin_df = DataFrame(levels)
cabin_df.columns = ['Cabin']
print(cabin_df.count())
#sns.factorplot('Cabin',data=cabin_df,palette='winter_d')
sns.catplot('Cabin',data=cabin_df,kind="count",palette='winter_d')
```

    Cabin    204
    dtype: int64
    




    <seaborn.axisgrid.FacetGrid at 0x2026a6f80b8>




![png](/images/titanic/output_28_2.png)


Es interesante notar que tenemos un valor de cubierta 'T' allí que no tiene sentido, podemos eliminarlo con el siguiente código:


```python
# Redefinir cabin_df como todo menos donde la fila era igual a 'T'
cabin_df = cabin_df[cabin_df.Cabin != 'T']
# volvamos a graficar
# sns.factorplot('Cabin',data=cabin_df,palette='summer')
sns.catplot('Cabin',data=cabin_df,kind="count",palette='summer')
```




    <seaborn.axisgrid.FacetGrid at 0x2026bc174a8>




![png](/images/titanic/output_30_1.png)


Nota rápida: utilicé 'winter_d' y 'summer' como mis paletas, pero puede elegir la paleta que desee. Consulte este enlace para ver más nombres de paletas, puede agregar '_d' al final de cualquier nombre de paleta para oscurecerlo.

Link: http://matplotlib.org/users/colormaps.html

Genial ahora que hemos analizado la distribución por mazos, sigamos adelante y respondamos nuestra tercera pregunta:   
   3.) ¿De dónde vienen las pasajeros?


```python
# Veamos nuevamente nuestros datos originales
titanic_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
  </tbody>
</table>
</div>



Observe aquí que la columna Embarcada tiene valores C, Q y S. Al leer sobre el proyecto en Kaggle, notará que estos significan Cherburgo, Queenstown, Southhampton.


```python
# Ahora podemos hacer un diagrama de factor rápido para ver los resultados, tenga en cuenta el argumento x_order, utilizado para tratar con los valores de NaN
#sns.factorplot('Embarked',data=titanic_df,hue='Pclass',x_order=['C','Q','S'])
sns.catplot('Embarked',hue='Pclass',data=titanic_df,kind="count",palette='summer')
```




    <seaborn.axisgrid.FacetGrid at 0x2026bdf0048>




![png](/images/titanic/output_35_1.png)


Un hallazgo interesante aquí es que en Queenstown, casi todos los pasajeros que abordaron allí eran de tercera clase. Sería interesante ver la economía de esa ciudad en ese período de tiempo para una mayor investigación.

Ahora echemos un vistazo a la cuarta pregunta:

    4.) ¿Quién estaba solo y quién estaba con la familia?


```python
# Comencemos agregando una nueva columna para definir solo

# Agregaremos la columna padre / hijo con la columna sibsp
titanic_df['Alone'] =  titanic_df.Parch + titanic_df.SibSp
titanic_df['Alone']
```




    0      1
    1      1
    2      0
    3      1
    4      0
          ..
    886    0
    887    0
    888    3
    889    0
    890    0
    Name: Alone, Length: 891, dtype: int64



Ahora sabemos que si la columna Alone es cualquier cosa menos 0, entonces el pasajero tenía familia a bordo y no estaba solo. Cambiemos la columna ahora para que si el valor es mayor que 0, sepamos que el pasajero estaba con su familia, de lo contrario, estarían solos.


```python
# Observemos que >0 o ==0 para poner el estatus de solo
titanic_df['Alone'].loc[titanic_df['Alone'] >0] = 'With Family'
titanic_df['Alone'].loc[titanic_df['Alone'] == 0] = 'Alone'

# Tenga en cuenta que está bien ignorar un error que a veces aparece aquí. Para más información mira este enlace
url_info = 'http://stackoverflow.com/questions/20625582/how-to-deal-with-this-pandas-warning'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-79-49295f691e4f> in <module>
          1 # Observemos que >0 o ==0 para poner el estatus de solo
    ----> 2 titanic_df['Alone'].loc[titanic_df['Alone'] >0] = 'With Family'
          3 titanic_df['Alone'].loc[titanic_df['Alone'] == 0] = 'Alone'
          4 
          5 # Tenga en cuenta que está bien ignorar un error que a veces aparece aquí. Para más información mira este enlace
    

    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\ops\common.py in new_method(self, other)
         62         other = item_from_zerodim(other)
         63 
    ---> 64         return method(self, other)
         65 
         66     return new_method
    

    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\ops\__init__.py in wrapper(self, other)
        527         rvalues = extract_array(other, extract_numpy=True)
        528 
    --> 529         res_values = comparison_op(lvalues, rvalues, op)
        530 
        531         return _construct_result(self, res_values, index=self.index, name=res_name)
    

    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\ops\array_ops.py in comparison_op(left, right, op)
        245 
        246     elif is_object_dtype(lvalues.dtype):
    --> 247         res_values = comp_method_OBJECT_ARRAY(op, lvalues, rvalues)
        248 
        249     else:
    

    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\ops\array_ops.py in comp_method_OBJECT_ARRAY(op, x, y)
         55         result = libops.vec_compare(x.ravel(), y, op)
         56     else:
    ---> 57         result = libops.scalar_compare(x.ravel(), y, op)
         58     return result.reshape(x.shape)
         59 
    

    pandas\_libs\ops.pyx in pandas._libs.ops.scalar_compare()
    

    TypeError: '>' not supported between instances of 'str' and 'int'



```python
# Let's check to make sure it worked
titanic_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
      <th>Alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
      <td>With Family</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
      <td>With Family</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
      <td>Alone</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
      <td>With Family</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
      <td>Alone</td>
    </tr>
  </tbody>
</table>
</div>




```python
# ¡Ahora obtengamos una visualización simple!
#sns.factorplot('Alone',data=titanic_df,palette='Blues')
sns.catplot('Alone',data=titanic_df,kind="count",palette='summer')
```




    <seaborn.axisgrid.FacetGrid at 0x2026bf39f28>




![png](/images/titanic/output_41_1.png)


¡Buen trabajo! Ahora que hemos analizado a fondo los datos, veamos la pregunta más interesante (y abierta):   
* ¿Qué factores ayudaron a alguien a sobrevivir al hundimiento? 


```python
# Comencemos creando una nueva columna para propósitos de legibilidad a través del mapeo
titanic_df["Survivor"] = titanic_df.Survived.map({0: "no", 1: "yes"})

# Vamos a obtener una visión general rápida de sobrevivido vs muerto.
sns.catplot('Survivor',kind='count',data=titanic_df,palette='Set1')
```




    <seaborn.axisgrid.FacetGrid at 0x2026bf06748>




![png](/images/titanic/output_43_1.png)


Así que murieron muchas más personas que las que sobrevivieron. Veamos si la clase de los pasajeros tuvo un efecto en su tasa de supervivencia, ya que la película Titanic popularizó la noción de que los pasajeros de tercera clase no lo hicieron tan bien como sus homólogos de primera y segunda clase.


```python
# Let's use a factor plot again, but now considering class
#sns.factorplot('Pclass','Survived',data=titanic_df)
sns.catplot('Pclass','Survived',data=titanic_df,kind='point')
```




    <seaborn.axisgrid.FacetGrid at 0x2026c0fbc50>




![png](/images/titanic/output_45_1.png)


¡Parece que las tasas de supervivencia para la tercera clase son sustancialmente más bajas! Pero tal vez este efecto sea causado por la gran cantidad de hombres en la tercera clase en combinación con la primera política de mujeres y niños. Usemos 'hue' para obtener una imagen más clara de esto.


```python
# Usemos nuevamente una gráfica de factores, pero ahora considerando la clase y el género
#sns.factorplot('Pclass','Survived',hue='person',data=titanic_df)
sns.catplot('Pclass','Survived',hue='person',data=titanic_df,kind='point')
```




    <seaborn.axisgrid.FacetGrid at 0x2026e124be0>




![png](/images/titanic/output_47_1.png)


A partir de estos datos, parece que ser hombre o estar en tercera clase no fueron favorables para la supervivencia. Incluso independientemente de la clase, el resultado de ser hombre en cualquier clase disminuye dramáticamente sus posibilidades de supervivencia.

¿Pero qué hay de la edad? ¿Ser joven o mayor tuvo un efecto en la tasa de supervivencia?


```python
# Usemos una gráfica lineal sobre edad versus supervivencia
sns.lmplot('Age','Survived',data=titanic_df)
```




    <seaborn.axisgrid.FacetGrid at 0x2026e18def0>




![png](/images/titanic/output_49_1.png)


Parece que hay una tendencia general de que cuanto más viejo era el pasajero, menos probable era que sobreviviera. Avancemos y usemos el tono para observar el efecto de la clase y la edad.


```python
# Usemos una gráfica lineal sobre la edad versus la supervivencia usando el tono para la separación de clases
sns.lmplot('Age','Survived',hue='Pclass',data=titanic_df,palette='winter')
```




    <seaborn.axisgrid.FacetGrid at 0x2026f256a58>




![png](/images/titanic/output_51_1.png)


¡También podemos usar el argumento x_bin para limpiar esta figura y tomar los datos y agruparlos por edad con un estándar adjunto


```python
# Usemos una gráfica lineal sobre la edad versus la supervivencia usando el tono para la separación de clases
generations=[10,20,40,60,80]
sns.lmplot('Age','Survived',hue='Pclass',data=titanic_df,palette='winter',x_bins=generations)
```




    <seaborn.axisgrid.FacetGrid at 0x2026f283860>




![png](/images/titanic/output_53_1.png)


Interesante encontrar en los pasajeros mayores de primera clase! ¿Qué pasa si relacionamos género y edad con el conjunto de supervivencia?


```python
sns.lmplot('Age','Survived',hue='Sex',data=titanic_df,palette='winter',x_bins=generations)
```




    <seaborn.axisgrid.FacetGrid at 0x2026f3701d0>




![png](/images/titanic/output_55_1.png)


¡Increíble! hemos obtenido algunas ideas realmente geniales sobre cómo el género, la edad y la clase se relacionan con la posibilidad de supervivencia de los pasajeros. 

Ahora toma el control: Responda las siguientes preguntas con pandas y seaborn:

    1.) ¿La cubierta tuvo un efecto en la tasa de supervivencia de los pasajeros? ¿Esta respuesta coincide con tu intuición?
    2.) ¿Tener un miembro de la familia aumentó las probabilidades de sobrevivir al accidente?
    

### ¡Fantástico trabajo en tu primer intento en un proyecto de análisis de datos! Continúe y siga jugando con los datos o intente seguir junto con el tutorial de aprendizaje del kit de ciencia ficción de Kaggle para estos datos (lo veremos a través de una perspectiva de aprendizaje automático más adelante en el curso)

#### Finalmente, te dejo con un gif de mi escena favorita de la película Titanic


```python
from IPython.display import Image
Image(url='http://i.imgur.com/DGNjT.gif')
```




<img src="http://i.imgur.com/DGNjT.gif"/>



#### Te recomiendo revisar el proyecto mas votado que se realizó en Kaggle
https://www.kaggle.com/startupsci/titanic-data-science-solutions
