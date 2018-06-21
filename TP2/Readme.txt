~~~~~~~TP2~~~~~~~

1) Entrar en DataAnalysis para crear la matriz que contiene las postulaciones verdaderas y postulaciones falsas.
   Para ello, entrar en 'Generar_avisos_postulantes'. Si es necesario persistir los archivos por problemas de memoria tratar de localizarlos en alguna 	  carpeta aparte como 'temporal'. Para crear una x cantidad de postulaciones en la ultima línea poner:
	
	amount = merge_postulants_ads.sample(x)
   
   Y guardar el archivo como 'postulantesXM.csv' (La M de millones). Por ej: amount.to_csv("postulantes2M.csv", index=False)
   
   Luego crear las postulaciones falsas en el archivo 'Generar_nopostulaciones_Reducido'. Ejecutar todo, solo que en la parte de 'get_randoms_ids()'
   hay que determinar la cantidad de randoms(postulaciones falsas) que queremos. DENTRO DE LA FUNCION:
   
   for i in range (0,NUMERO QUE QUEREMOS):
        numero = random.randrange(0,371380) #Verificar el máximo número que puede llegar
        idpostulante = df_postulants['idpostulante'][numero]
        dic['idpostulante'].append(idpostulante)
        numero2 = random.randrange(0,19634) #Verificar el máximo número que puede llegar
        idaviso = df_ads['idaviso'][numero2]
        dic['idaviso'].append(idaviso)

   Al final persistir el data frame al igual que antes. Por ej: random_postulant_ad.to_csv("no_postulantes2M.csv",index = False)

   Para obtener la matriz gigante, ir al notebook 'Mergear_postulaciones_nopostulacionesReducido'. Y guardar el archivo final como:
   total.to_csv("dataXM.csv", index = False) donde X es la cantidad de datos sumados (postulaciones + postulaciones falsas)

   Para obtener los datos a testear, ir a la carpeta Test, y 'Generar_csv_test'. (ESTA CORROMPIDO HAY QUE HACERLO OTRA VEZ)

2) Para mappear la data, entrar en MapDataAnalysis. En 'codificar_entrenamiento' ejecutar todo (excepto que se quiera cambiar algun mappeo) y guardar como : total.to_csv('MappedDataXM.csv'), donde X es la cantidad de datos sumados (postulaciones + postulaciones falsas). 
IMPORTANTE: Si se cambió el mappeo de los datos por algún motivo, habria que especificarlo en el nombre del archivo!!
   Realizar lo mismo para los test, solo que el archivo final es: test.to_csv('MappedTest.csv',index = False)
   La advertencia de IMPORTANTE es válida para los test tambien!

3) En Algorithms, crear un notebook con un nuevo algoritmo o utilizar alguno ya hecho. Llamar a los archivos mappeados y entrenar el algoritmo. Usar el score entre el X_test e y_test para el Excel. (Tambien anotar los hiperparametros). Una vez entrenado, predecimos los tests con 'predict_proba' y solo queremos un csv que contenga ID,sepostulo (aqui la probabilidad de los 1). Y guardar el archivo en:
	
	test.to_csv('../Predictions/DecisionTree4M.csv', index=False), indicando el nombre del algoritmo, la cantidad de datos y si hay alguna variante como reducido los features aclararlo. En el excel completar todos los datos!

4)Subirlo a kaggle y disfrutar del score!
 
