 p23_BML: 
----------
# BERT를 이용한 음원 가사 다중 감정(emotion) 예측

본 연구는 음원 스트리밍 서비스의 Top100 차트에 진입하는 음원들의 내재적 특성을 알아보기 위해 진행되었다. 
자연어 처리 딥러닝 모델인 BERT를 활용하여 음원의 가사가 전달하는 감정을 인식 및 추출하였다. 
따라서 본 연구는 정형 데이터인 음원의 오디오 특성뿐만 아니라 비정형 데이터인 가사(lyrics)의 특성도 함께 고려했다는 점에서 의의가 있다.

 Russell 감정 모델에 기반한 라벨링된 데이터 확보에 어려움이 있어,음원 감정 분류 범주로 Paul Ekman(1992)의 6가지 감정(anger, disgust, fear, hapinness, sadness, surprise) 모델을 사용했다.

본 연구를 통해 스트리밍 음원 사이트의 Top 100 차트에 진입하는 음원들의 내재적 특성을 살펴보았다. 
음원의 내재적 특성으로 정형 데이터인 오디오 특징과 비정형 데이터인 가사의 특징을 함께 고려하였다. 
일부(28) 음원을 제외한 대다수 음원은 가사에 복합적인 감정을 담고 있었다.
음원의 유명한 정도(popularity)에 대한 분석을 종합해봤을 때, 차트에 진입하는 동력은 음원의 내재적 특성에 있다고 보기 어렵다. 
즉 노래만 좋다고 해서 높은 성과를 거둘 수는 없다는 것이다. 
음원의 흥행은 음원의 내재적 특성 단독보다는, 외부적 요인(마케팅, 아티스트의 팬덤 등) 또는 그와의 상호작용에 더 큰 영향을 받는 것으로 예상된다. 

<br>

### 데이터
- 음원데이터: Spotify API 서비스를 활용하여, Spotify의 “Top Hits of 2015”, “Top Hits of 2016”, “Top Hits of 2017”, “Top Hits of 2018”, “Top Hits of 2019” 재생목록 각각에 수록된 100개의 음원과 각 음원의 정보를 수집하였다.
- 가사데이터: Spotify API 서비스에서 음원의 가사 정보를 제공하지 않아, Genius API 서비스를 활용하여 각 음원의 track_name과 artist_name을 기준으로 가사를 크롤링했다.

### 모델
- Emotion English DistilRoBERTa-base: Hugging Face에 업로드된, 영어 텍스트 데이터에서 감정을 분류하는 모델이다. DistilRoBERTa-base을 파인튜닝하여, Ekman(1992)의 감정 모델에 기반한 6가지 감정(anger, disgust, fear, joy, sadness, surprise)과 neutral 감정을 예측한다.

  ```python
   @misc{hartmann2022emotionenglish,
    author={Hartmann, Jochen},
    title={Emotion English DistilRoBERTa-base},
    year={2022},
    howpublished = {\url{https://huggingface.co/j-hartmann/emotion-english-distilroberta-base/}},
  }
  ```
