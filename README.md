**Para instalar o Uber Ludwig a partir do fonte do Github, execute o comando abaixo:**
```
pip install https://github.com/erichans/ludwig/archive/master.zip
```
Exemplo de experimentação de modelos com o ludwig via linha de comando:

**MNIST:**
```
ludwig experiment --experiment_name mnist_base --data_train_csv  mnist_dataset_training.csv --data_test_csv mnist_dataset_testing.csv  --model_definition_file model_definition.yml
```
**ACHADOS:**
```
ludwig experiment --experiment_name achados --data_train_csv dados_treino_Achados.csv --data_validation_csv dados_validacao_Achados.csv --data_test_csv dados_teste_Achados.csv -mdf model_definition.yaml
```

**Exemplo de servir o modelo Tensorflow usando REST:**
<br/>Executar antes a instalação de um utilitário necessário ao ludwig (?): <br/>
**```pip install email-validator```**

**MNIST:**
```
ludwig serve -m results\mnist_base_run_0\model\
```
**ACHADOS:**
```
ludwig serve -m results\achados_run_0\model\
```
**Exemplo de requisição para o modelo para MNIST:**
```
curl http://0.0.0.0:8000/predict -X POST -F 'image_path=@testing/9/6682.png'
```
**Exemplo de requisição para o modelo para ACHADOS:**
```
curl http://0.0.0.0:8000/predict -X POST -F 'ACHADO=Inadequação da pesquisa de preço em pregões realizados pela Secretaria de Saúde de Presidente Figueiredo  AM' 
```

**Exemplos de visualização do Ludwig:**

**Learning Rate Curve:**
```ludwig visualize --visualization learning_curves --model_names mnist_base_run_0 mnist_base_run_1 --training_statistics results\mnist_base_run_0\training_statistics.json results\mnist_base_run_1\training_statistics.json --field label```

**Confusion Matrix:**
```ludwig visualize --visualization confusion_matrix --top_n_classes 10 --test_statistics results\mnist_base_run_0\test_statistics.json --ground_truth_metadata mnist_dataset_training.json```

**Compare Performance:**
```ludwig visualize --visualization compare_performance --model_names mnist_base_run_0 mnist_base_run_1 --test_statistics results\mnist_base_run_0\test_statistics.json results\mnist_base_run_1\test_statistics.json --field label```

**Compare Models:**
```ludwig visualize -v compare_performance -tes results\mnist_base_run_0\test_statistics.json results\mnist_base_run_1\test_statistics.json -mn mnist_base_run_0 mnist_base_run_1 -f label```

**Compare classifiers performance from probs:**
```ludwig visualize --visualization compare_classifiers_performance_from_prob --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --probabilities results\mnist_base_run_0\label_probabilities.csv results\mnist_base_run_1\label_probabilities.csv --test_statistics results\mnist_base_run_0\test_statistics.json results\mnist_base_run_1\test_statistics.json```

**Compare classifiers performance from preds:**
```ludwig visualize --visualization compare_classifiers_performance_from_pred --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --ground_truth_metadata mnist_dataset_training.json --predictions results\mnist_base_run_0\label_predictions.npy results\mnist_base_run_1\label_predictions.npy```

**Compare Classifier Predictions:**
```ludwig visualize --visualization compare_classifiers_predictions --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --predictions results\mnist_base_run_0\label_predictions.csv results\mnist_base_run_1\label_predictions.csv```

**Compare Classifier Predictions from distributions:**
```ludwig visualize --visualization compare_classifiers_predictions_distribution --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --predictions results\mnist_base_run_0\label_predictions.npy results\mnist_base_run_1\label_predictions.npy```

**Confidence thresholding:**
```ludwig visualize --visualization confidence_thresholding --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --probabilities results\mnist_base_run_0\label_probabilities.csv results\mnist_base_run_1\label_probabilities.csv```

**ROC Curves:**
```ludwig visualize --visualization roc_curves --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --probabilities results\mnist_base_run_0\label_probabilities.csv results\mnist_base_run_1\label_probabilities.csv```

**Calibration plot (Multiclass) + Brier Score:**
```ludwig visualize --visualization calibration_multiclass --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth mnist_dataset_testing.hdf5 --field label --probabilities results\mnist_base_run_0\label_probabilities.csv results\mnist_base_run_1\label_probabilities.csv```

**Frequency vs F1 Score:**
```ludwig visualize --visualization frequency_vs_f1 --model_names mnist_base_run_0 mnist_base_run_1 --ground_truth_metadata mnist_dataset_training.json --field label --top_n_classes 10 --test_statistics results\mnist_base_run_0\test_statistics.json --ground_truth_metadata mnist_dataset_training.json```

