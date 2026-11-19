# CS3SY26_ProjectProposal by Aline Teresa Mendoza from CS Unit of PSHS


## Project Proposal Template: 

### Project Title or Name of the Application	: Cryptographic Decoder
### Section			   	      : Sodium
### Group Members			    : SALONGA, Jian Achilles; TANDOG, Johannes Brylle; TICZON, Christopher Manuel
### Date (Proposal Date)  : Nov 20, 2026

### Project Description:

- Our Cryptographic Decoder is a program designed to simplify the process of decryption. In today's world where data privacy is seen everywhere, cybersecurity professionals, cryptanalysts, and hobbyists regularly encounter encrypted texts requiring immediate decoding. Our software allows users to detect the overall cipher type and apply appropriate decoding methods to transform the encrypted data into human-readable messages.

- System Features:
  - Cipher Detection & Algorithm Management: Detects potential ciphers, takes into account available decoding algorithms, selects a viable algorithm, decodes the encrypted data, and manages a history of operations.
  - Pattern Analysis: Evaluates inputs using n-gram frequencies, entropy scores, and confidence metrics to identify patterns.
  - Multi-Format Decoding: Provides a decoder engine supporting AES, Base64, and Caesar ciphers, including specific helpers such as key derivation, padding checks, and brute-force attempts.
  - Interactive User Interface: Offers a dashboard to get input strings, select ciphers, display decoded outputs or error messages, toggle UI themes, and export reports.

  System Components (Classes):
  1. CipherManager (overall controller)
    Attributes:
      - supportedCiphers (list): Collection of available cipher algorithms
      - historyLog (list): Record of past cipher inspections or decoding
      - algorithm (str): Identifier or name of the currently chosen algorithm
      - activeDecoder (DecoderCore): Reference to active decoder instance
      - analyzer (FrequencyAnalyzer): Reference to the text pattern and frequecy analyzer
    Methods:
      - detect_cipher(): Inspects input text to identify likely cipher types
      - register_algorithm(): Adds a new cipher decoder algorithm to the supported list
      - select_algorithm(): Chooses which algorithm/decoder to use
      - execute_decoder(): Runs the decoding process on the target input
      - clear_history(): Clears stored entries in historyLog
  
  2. DecoderCore (engine of decoder)
    Attributes:
      - cipherText (str): The encoded/encrypted input string
      - key (str): Key material used for decoding/decryption
      - decodedOutput (str): Resulting plaintext or decoded string 
      - isValid (bool): Indicates whether the input or decoding state is valid
    Methods:
      - decode(): Abtract/base operation to transform cipherText into decodedOutput
      - validate_input(): Checks whether the input string and parameters are valid
      - get_data(): Retrieves decoder data/results
      - reset(): Resets decoder state and fields

  3. Concrete Decoder Subclasses (inherit from DecoderCore)
    - AESDecoder:
      Attributes: keySize (int), mode (str), iv (str)
      Methods: decode(), derive_key()
    - Base64Decoder:
      Attributes: encodingFormat (str), urlSafe (bool)
      Methods: decode(), check_padding()
    - CaesarDecoder:
      Attributes: shift (int), alphabet (str)
      Methods: decode(), brute-force()

  4. FrequencyAnalyzer (designated for analyzing patterns and n-gram frequencies)
    Attributes:
      - targetText (str): String being analyzed
      - ngramFrequency (dict): Mapping of n-grams to their observed frequencies
      - entropyScore (float): Calculated entropy measure of the text
      - confidenceScore (float): Confidence rating for pattern/cipher assessment
    Methods:
      - calculate_entropy(): Computes the entropy score of targetText
      - frequency_distribution(): Builds the n-gram frequency distribution
      - detect_pattern(): Identifies recurring patterns in the text

  5. UserInterface (UI; visual display of the code)
    Attributes:
      - inputBuffer (str): Text entered by the user for inspection/decoding
      - outputDisplay (str): Formatted output shown to the user
      - currentTheme (str): Active visual theme setting
      - selectedCipher (str): Cipher option currently selected in the UI
      - errorMessage (str): Error text displayed when data validation fails
    Methods:
      - load_dashboard(): Initializes and renders the main interface
      - capture_input(): Reads user input info
      - display_results(): Updates outputDisplay with decoding or analysis results
      - export_report(): Exports inspection/decoding results as a report
      - toggle_theme(): Switches currentTheme

  How they Interact/Relationships:
  1. Aggregation
    - Relationship: CipherManager and DecoderCore
  2. Directed Assosciation
    - Relationship 1: CipherManager and FrequencyAnalyzer
    - Relationship 2: CipherManager and UserInterface
  3. Inheritance
    - Relationship 1: AESDecoder and DecoderCore
    - Relationship 2: Base64Decoder and DecoderCore
    - Relationship 3: CaesarDecoder and DecoderCore

  Expected Outputs:
  - Decoded Strings
  - Cipher Detection & Statistical Metrics
  - Validation & Error Feedback
  - Session History & Exported Reports

- • Cybersecurity Professionals/Students: People learning, teaching, or using cryptograhy, cryptanalysis, and encoding standards for their requirements.
  
  - Cryptanalysts: Professionals who analyze ciphers, encryption systems, and security implementations to find weaknesses and access encrypted data without knowing the key.
  - Hobbysists: Cryptography enthusiasts who need fast and relaible tools to decode cipher/cipher layers during competitions or for games.
  - Software Developers: Professionals needing a quick tool to inspect strings for ciphers in their software/programs.

- Class Diagram: ![Class Diagram of Cryptographic Decoder](image.png)

### Goals:

Describe the long term outcomes of your project followed by a couple of objectives to meet the goals stated in this paragraph

- Objective 1:
- Objective 2:
- Objective n:

[Click here for Rubrics and Sample projects](https://docs.google.com/document/d/1xKd1CqK6DcNWS2_oJPBNtY5n3I3Hqiw8FY3W295Iqfk/edit?usp=sharing)
