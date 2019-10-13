# IUST-DeepFuzz
Welcome to our new file format fuzzer, IUST-DeepFuzz, a fuzzing framework based on the deep neural languages. This project belongs to my master thesis in software engineering: ["Automatic test data generation in file format fuzzers"](https://1drv.ms/b/s!AmpQstTzvc-T003nHGvhCeNP_ZpH). We can automatically generate new, valid, and various complex structure files, mainly PDF files, as test data to use in dynamic testing of real word application, e.g. PDF reader applications. For more information about both the theoretical and practical aspect of IUST-DeepFuzz, refer to the IUST-DeepFuzz relevant paper and thesis as in the following:

* [Format-aware Learn&Fuzz: Deep Test Data Generation for Efficient Fuzzing](https://arxiv.org/abs/1812.09961v2)
* [Automatic Test Data Generation in File Format Fuzzers](https://1drv.ms/b/s!AmpQstTzvc-T003nHGvhCeNP_ZpH) (In Persian)


## Thesis: Bring Deep Neural Network to Fuzz Testing
Fuzz testing (Fuzzing) is a dynamic software testing technique. In this technique with repeated generation and injection of malformed test data to the software under test (SUT), we are looking for the possible faults and vulnerabilities. To this goal, fuzz testing requires varieties of test data. The most critical challenge is to handle the complexity of the file structures as program input. Surveys have revealed that many of the generated test data in these cases follow restricted numbers and superficial paths, because of being rejected by the parser of SUT in the initial stages of parsing. Using the grammatical structure of input files to generate test data lead to increase code coverage. However, often, the grammar extraction is performed manually, which is a time consuming, costly and error-prone task. 

In this thesis, we proposed an automated method for hybrid test data generation. To this aim, we apply neural language models (NLMs) that are constructed by recurrent neural networks (RNNs). The proposed models by using deep learning techniques can learn the statistical structure of complex files and then generate new textual test data, based on the grammar, and binary data, based on mutations. Fuzzing the generated data is done by two newly introduced algorithms, called neural fuzz algorithms that use these models. We use our proposed method to generate test data, and then fuzz testing of MuPDF complicated software which takes portable document format (PDF) files as input. To train our generative models, we gathered a large corpus of PDF files. Our experiments demonstrate that the data generated by this method leads to an increase in the code coverage, more than 7%, compared to state-of-the-art file format fuzzers such as American fuzzy lop (AFL). Experiments also indicate a better learning accuracy of simpler NLMS in comparison with the more complicated encoder-decoder model and confirm that our proposed models can outperform the encoder-decoder model in code coverage when fuzzing the SUT.


## Getting Started
In the current release (0.3.0) you can use IUST-DeepFuzz for test data generation and then fuzzing every application.

### Install
You need to have Python 3.6.x and and up-to-date TensorFlow and Keras frameworks on your computer.
* Install [Python 3.6.x](https://www.python.org/)
* Install [TensorFlow](https://www.tensorflow.org/)
* Install [Keras](https://keras.io/)
* Clone the IUST-DeepFuzz repository: `git clone https://github.com/m-zakeri/iust_deep_fuzz.git` or download the latest version https://github.com/m-zakeri/iust_deep_fuzz.git
* IUST-DeepFuzz is almost ready for test data generation!

### Running
* Configure the `config.py` work with your dataset and to set other paths settings.
* Find the script of specific algorithm that you need. 
* Run the script in command line: `python script_name.py`
* Wait until your file format learn and your test data is generate!

#### Available Pre-trained Models
A pre-trained model is a model that was trained on a large benchmark dataset to solve a problem similar to the one that we want to solve. For the time being, we provided some pre-trained model for PDF file format. Our best trained model is available at [model_checkpoint/best_models](model_checkpoint/best_models)

#### Availbale Fuzzing Scripts
ISUT-DeepFuzz has implemented four new deep models and two new fuzz algorithms: DataNeuralFuzz and MetadataNeuralFuzz as our contribution in mentioned thesis. The following algorithms to generate and fuzz test data are available in the current release (r0.3.0):
* `data_neural_fuzz.py`: To implement the DataNeuralFuzz algorithm for fuzzing data in the files.
* `metadata_neural_fuzz.py`: To implement MetadataNeuralFuzz for fuzzing metadata in the files.
* `learn_and_fuzz_3_sample_fuzz.py`: To implement SampleFuzz algorithm introduced in https://arxiv.org/abs/1701.07232. 

#### Available Dataset
Various file format for learning with IUST-DeepFuzz and then fuzz testing is available at [dataset directory](dataset).


## How It Works?

### The PDF File Generation Process 
 ![amazing_test_data_generation_process](docs/figs/amazing_test_data_generation_process.gif)


### New PDF Files
![generated_pdfs](docs/figs/amazing_generated_test_data.png)



### FAQs
This repository is under *active development* and it dose not documented well. If you have downloaded source code or have forked it and have any questions, then feel free to email me (*m-zakeri@live.com*) and get more information. You may see the main [references](REFERENCES.md) or look at our large [test corpus](dataset).

July 5, 2019
