# stt-models-locals

Get the best STT model for your system.

## Usage

It's mainly used by a program to find the best STT model for the local of your system.

_i.e._

 - `$LANG = "en_US.UTF-8" -> 'en': "English STT v1.0.0-huge-vocab"`

 - `$LANG = "fr_CH.UTF-8" -> 'fr': "French STT v0.9"`

`models.json` looks like this:
```json
{
    "locals": {
        "en": "English"
    },
    "models": {
        "English": {
                "language": "English",
                "name": "English STT v1.0.0-huge-vocab",
                "version": "v1.0.0-huge-vocab",
                "creator": "Coqui",
                "acoustic": "https://coqui.gateway.scarf.sh/english/coqui/v1.0.0-huge-vocab/model.tflite",
                "scorer": "https://coqui.gateway.scarf.sh/english/coqui/v1.0.0-huge-vocab/huge-vocabulary.scorer"
            }
    }
}
```

You can use something like python to get the model card for your language.

```python
import os

I18N, L10N = (x for x in os.environ.get('LANG', "en_EN.UTF-8").split(".")[0].split("_"))

def return_local_model_card():
    r = request.urlopen(MODELS_URL)
    rb = r.read()
    json_models = json.loads(rb.decode('utf-8'))
    model_lang = loc_models['locals'].get(I18N)
    model_card = json_models['models'].get('model_lang')
    return model_card

>>> return_local_model_card()

# you can then use the model manager of STT to download the models.
from coqui_stt_model_manager.modelmanager import ModelManager, ModelCard

manager = ModelManager()
manager.download_model(return_local_model_card())
```

Or simply use [`listen`](https://gitlab.com/waser-technologies/technologies/listen).

```zsh
pip install git+https://gitlab.com/waser-technologies/technologies/listen.git
LANG="fr_CH.UTF-8" python -m listen.STT.as_service
--- in another terminal session ---
listen
```

## Source

https://raw.githubusercontent.com/wasertech/stt-models-locals/main/models.json

## Languages

| `$LANG` | Language | STT Model |
| ------- | -------- | --------- |
| am | Amharic | Amharic STT v0.1.0 |
| eu | Basque | Basque STT v0.1.1 |
| bn | Bengali | Bengali STT v0.1.0 |
| br | Breton | Breton STT v0.1.1 |
| ca | Catalan | Catalan STT v0.14.0 |
| cv | Chuvash | Chuvash STT v0.1.1 |
| cs | Czech | Czech STT v0.2.0 |
| dv | Dhivehi | Dhivehi STT v0.1.1 |
| nl | Dutch | Dutch STT v0.0.1 |
| en | English | English STT v1.0.0-huge-vocab |
| et | Estonian | Estonian STT v0.1.1 |
| fi | Finnish | Finnish STT v0.1.1 |
| fr | French | French STT v0.9 |
| fy | Frisian | Frisian STT v0.1.1 |
| ka | Georgian | Georgian STT v0.1.1 |
| de | German | German STT v0.0.1 |
| el | Greek | Greek STT v0.1.1 |
| hu | Hungarian | Hungarian STT v0.1.1 |
| id | Indonesian | Indonesian STT v0.1.1 |
| ga | Irish | Irish STT v0.1.1 |
| it | Italian | Italian STT 2020.8.7 |
| rw | Kinyarwanda | Kinyarwanda STT v0.0.1 |
| kv | Komi | Komi-Zyrian STT v0.0.1 |
| ky | Kyrgyz | Kyrgyz STT v0.1.1 |
| lv | Latvian | Latvian STT v0.1.1 |
| lt | Lithuanian | Lithuanian STT v0.1.1 |
| lg | Luganda | Luganda STT v0.1.1 |
| mt | Maltese | Maltese STT v0.1.1 |
| mn | Mongolian | Mongolian STT v0.1.1 |
| or | Odia | Odia STT v0.1.1 |
| pl | Polish | Polish STT v0.0.1 |
| pt | Portuguese | Portuguese STT v0.1.1 |
| ro | Romanian | Romanian STT v0.1.1 |
| wae | Romansh-vallader | Romansh Vallader STT v0.1.0 |
| ru | Russian | Russian STT v0.1.0 |
| sah | Sakha | Sakha STT v0.1.1 |
| sl | Slovenian | Slovenian STT v0.1.1 |
| es | Spanish | Spanish STT v0.0.1 |
| sw | Swahili | Swahili STT v0.8 |
| ta | Tamil | Tamil STT v0.1.0 |
| tt | Tatar | Tatar STT v0.1.0 |
| th | Thai | Thai STT v0.1.0 |
| tr | Turkish | Turkish STT v0.1.0 |
| uk | Ukrainian | Ukrainian STT v0.4 |
| hsb | Upper-sorbian | Upper Sorbian STT v0.1.0 |
| cy | Welsh | Welsh STT v21.03 |
| wo | Wolof | Wolof STT v0.1.0 |
| yo | Yoruba | Yoruba STT v0.1.0 |

## Contributions

If you see a mistake or miss your favorite language please add a [new issue](https://github.com/wasertech/stt-models-locals/issues/new/choose). PR are also welcome. 
