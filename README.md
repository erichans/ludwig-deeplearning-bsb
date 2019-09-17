Para instalar o Uber Ludwig a partir do fonte do Github, execute o comando abaixo:
pip install https://github.com/uber/ludwig/archive/master.zip

Exemplo de expermentação de modelos com o ludwig via linha de comando:

MNIST:
ludwig experiment --experiment_name mnist_base --data_train_csv  mnist_dataset_training.csv --data_test_csv mnist_dataset_testing.csv  --model_definition_file model_definition.yml

ACHADOS:
ludwig experiment --experiment_name achados --data_train_csv achados-train.csv --data_validation_csv achados-valid.csv -mdf model_definition.yaml 
