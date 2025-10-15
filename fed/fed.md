---
layout: default
title: "Fe de Erratas"
---

## Unidad 4. Aprendizaje no supervisado: modelos de agrupación y análisis de patrones

En Notebook (COLAB) del Ejemplo completo (síntesis de todas las lecciones) hay un error en el cálculo de las métricas. Hay que excluir, con el drop, siempre la columna del número de clúster, ya se diga k-means_label, Clúster...

silhouette = silhouette_score(df_scaled.drop(columns=['kmeans_labels']), df_scaled['kmeans_labels'])
print(f"Silhouette Score: {silhouette}")

davies_bouldin = davies_bouldin_score(df_scaled.drop(columns=['kmeans_labels']), df_scaled['kmeans_labels'])
print(f"Davies-Bouldin Score: {davies_bouldin}")

calinski_harabasz = calinski_harabasz_score(df_scaled.drop(columns=['kmeans_labels']), df_scaled['kmeans_labels'])
print(f"Calinski-Harabasz Score: {calinski_harabasz}")


Lo mismo sucede con las representaciones de los gráficos PCA, falta excluir dicha columna: 
pca.fit_transform(df_scaled.drop(columns=['kmeans_labels'], errors='ignore'))
