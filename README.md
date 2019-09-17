Para instalar o Uber Ludwig a partir do fonte do Github, execute o comando abaixo:
pip install https://github.com/uber/ludwig/archive/master.zip

Exemplo de expermentação de modelos com o ludwig via linha de comando:

MNIST:
ludwig experiment --experiment_name mnist_base --data_train_csv  mnist_dataset_training.csv --data_test_csv mnist_dataset_testing.csv  --model_definition_file model_definition.yml

ACHADOS:
ludwig experiment --experiment_name achados --data_train_csv dados_treino_Achados.csv --data_validation_csv dados_validacao_Achados.csv --data_test_csv dados_teste_Achados.csv -mdf model_definition.yaml


Exemplo de servir o modelo Tensorflow usando REST:
Executar antes a instalação de um utilitário necessário ao ludwig (?): pip install email-validator

MNIST:
ludwig serve -m results/mnist_base_run_0/model/

ACHADOS:
ludwig serve -m results/achados_run_0/model/

Exemplo de requisição para o modelo para MNIST:
curl http://0.0.0.0:8000/predict -X POST -F 'image_path=@testing/9/6682.png'

Exemplo de requisição para o modelo para ACHADOS:
curl http://0.0.0.0:8000/predict -X POST -F 'ACHADO=Inadequação da pesquisa de preço em pregões realizados pela Secretaria de Saúde de Presidente Figueiredo  AM' 
