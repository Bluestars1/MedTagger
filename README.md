![Build](https://github.com/OHNLP/MedTagger/workflows/Build/badge.svg)
# MedTagger

MedTagger contains a suite of programs that the Mayo Clinic NLP program has developed in 2013.
It includes three major components: MedTagger for indexing based on dictionaries, MedTaggerIE for
information extraction based on patterns, and MedTaggerML for machine learning-based named entity recognition.

# Build a Dictionary 
The updated release includes a dictionary based on MedLex, a corpus-driven semantic lexicon, that maps to OMOP Concept identifiers. MedTagger for indexing is built upon a fast string matching algorithm leveraging lexical normalization. The contextual annotator enables the detection of local context for concept entries detected. The new release of the dictionary maps to the OMOP Concept identifiers. For the detailed information of those concept identifiers, please visit http://athena.ohdsi.org. 


# Custom Ruleset Use Case - COVID 19 
MedTagger IE Pipelines use a custom ruleset format. An example ruleset of Coronavirus Diseases 19 (COVID 19) related symptoms (e.g. dry cough, fever, fatigue) 
can be found [here](https://github.com/OHNLP/MedTagger/tree/master/src/main/resources/medtaggerieresources/covid19) under the `/src/main/resources/medtaggerieresources/covid19` directory. These resources are what tells MedTagger
what to do/extract, and this directory is expected as input for the RULEDIR parameter 

# Installation and Use
#### Live demo for COVID-19 ruleset: https://ohnlp.github.io/ohnlptk/
#### Video demo: https://vimeo.com/392331446
1. Download the latest release from https://github.com/OHNLP/MedTagger/releases
2. Extract the zip file
3. Modify the `INPUTDIR`, `OUTPUTDIR`, and `RULEDIR` variables in `run_medtagger_win.bat` or `run_medtagger_unix_mac.sh`, as appropriate
    - `INPUT_DIR`: full directory path of input folder 
    - `OUTPUT_DIR`: full directory path of output folder
    - `RULES_DIR`: full directory path of 'Rule' folder
    
    Example for Mac:
    ```
    INPUTDIR="$YOUR_INPUT_DIRECTORY"
    OUTPUTDIR="$YOUR_OUTPUT_DIRECTORY"
    RULEDIR="$YOUR_MEDTAGGER_HOME/medtaggerieresources/covid19"
    ```
    
    Example for Windows:
    ```
    INPUTDIR="C:\$YOUR_INPUT_DIRECTORY\input"
    OUTPUTDIR="C:\$YOUR_OUTPUT_DIRECTORY\output"
    RULEDIR="C:\YOUR_MEDTAGGER_HOME\medtaggerieresources\covid19"
    ```
    
4. Run the batch file

    Mac/linux: 
    ```
    run_medtagger_unix_mac.sh
    ```
    
    Windows: 
    
    ```
    run_medtagger_win.bat
    ```
    


# For Developers
1. Clone this repository
2. You will need JDK8 or above, Apache Maven, and Apache Ant installed
3. To access github package repositories for dependency resolution, you will need to generate an appropriate github token with the read:packages permissions, and edit settings.xml appropriately by replacing `${env.SECRET_ACTOR}` with your github username and `${env.SECRET_TOKEN}` with the generated token.
4. When your modifications are complete, from the project root directory:
    - Run `mvn clean install -s settings.xml`
    - Run `ant dist`
    - A distribution zip will be created at `MedTagger.zip` in the root directory
    
   
# Reference
Liu H, Bielinski SJ, Sohn S, Murphy S, Wagholikar KB, Jonnalagadda SR, Ravikumar KE, Wu ST, Kullo IJ, Chute CG. An information extraction framework for cohort identification using electronic health records. AMIA Summits on Translational Science Proceedings. 2013;2013:149.

Wen A, Fu S, Moon S, El Wazir M, Rosenbaum A, Kaggal VC, Liu S, Sohn S, Liu H, Fan J. Desiderata for delivering NLP to accelerate healthcare AI advancement and a Mayo Clinic NLP-as-a-service implementation. npj Digital Medicine. 2019 Dec 17;2(1):1-7.
