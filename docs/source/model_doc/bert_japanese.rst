.. 
    Copyright 2020 The HuggingFace Team. All rights reserved.

    Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with
    the License. You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
    an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
    specific language governing permissions and limitations under the License.

BertJapanese
-----------------------------------------------------------------------------------------------------------------------

Overview
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The BERT models trained on Japanese text.

There are models with two different tokenization methods:

- Tokenize with MeCab and WordPiece. This requires some extra dependencies, `fugashi
  <https://github.com/polm/fugashi>`__ which is a wrapper around `MeCab <https://taku910.github.io/mecab/>`__.
- Tokenize into characters.

To use `MecabTokenizer`, you should ``pip install transformers["ja"]`` (or ``pip install -e .["ja"]`` if you install
from source) to install dependencies.

See `details on cl-tohoku repository <https://github.com/cl-tohoku/bert-japanese>`__.

Example of using a model with MeCab and WordPiece tokenization:

.. code-block::

  >>> import torch
  >>> from transformers import AutoModel, AutoTokenizer 

  >>> bertjapanese = AutoModel.from_pretrained("cl-tohoku/bert-base-japanese")
  >>> tokenizer = AutoTokenizer.from_pretrained("cl-tohoku/bert-base-japanese")

  >>> ## Input Japanese Text
  >>> line = "吾輩は猫である。"

  >>> inputs = tokenizer(line, return_tensors="pt")

  >>> print(tokenizer.decode(inputs['input_ids'][0]))
  [CLS] 吾輩 は 猫 で ある 。 [SEP]

  >>> outputs = bertjapanese(**inputs)

Example of using a model with Character tokenization:

.. code-block::

  >>> bertjapanese = AutoModel.from_pretrained("cl-tohoku/bert-base-japanese-char")
  >>> tokenizer = AutoTokenizer.from_pretrained("cl-tohoku/bert-base-japanese-char")

  >>> ## Input Japanese Text
  >>> line = "吾輩は猫である。"

  >>> inputs = tokenizer(line, return_tensors="pt")

  >>> print(tokenizer.decode(inputs['input_ids'][0]))
  [CLS] 吾 輩 は 猫 で あ る 。 [SEP]

  >>> outputs = bertjapanese(**inputs)

Tips:

- This implementation is the same as BERT, except for tokenization method. Refer to the :doc:`documentation of BERT
  <bert>` for more usage examples.

BertJapaneseTokenizer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. autoclass:: transformers.BertJapaneseTokenizer
    :members: 
