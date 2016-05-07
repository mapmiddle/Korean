* 한글과 관련된 여러가지 기능을 포함한 Python 라이브러리
* Python 2.7 을 기준으로 개발

# + Korean
1. 소개
  * 기본적인 한글 클래스
  * 자음과 모음 결합기능 지원
  * 각 초성, 중성, 종성 분해 및 추출, 변경 기능 지원

2. 사용
  * 생성
  ```
  import Korean
  
  s = Korean('안녕세상아')
  print s[0]
  >>> 안
  
  c1 = Korean.Syllable(letter='안')
  print c1
  >>> 안
  
  c2 = Korean.Syllable(phoneme_onset='ㅇ', phoneme_nucleus='ㅏ', phoneme_coda='ㄴ')
  print c2
  >>> 안
  ```
  
  * 초,중,종성 추출
  ```
  s = Korean('안녕세상아')
  print s[0].phoneme_onset
  >>> ㅇ
  
  print s[0].phoneme_nucleus
  >>> ㅏ
  
  print s[0].phoneme_coda
  >>> ㄴ
  ```
  
  * 초,중,종성 변경
  ```
  s = Korean('안녕세상아')
  s[0].phoneme_coda = 'ㄹ'
  s[0].combine()
  print s[0]
  >>> 알
  
  s.join()
  print s
  >>> 알녕세상아
  
  c = Korean.Syllable(letter='우')
  c.phoneme_nucleus += 'ㅓ'
  c.combine()
  print c
  >>> 워
  ```
  
  * 자음
# + CMU To Korean
1. 소개
  * Carnegie Mellon University 에서 제공하는 영어 발음기호를 이용해 영어를 한글 발음으로 변환하는 클래스
  * 발음 기호를 한글로 직역 했을때의 어색한 단어 일부 교정(Chocolate -> 초클랫, 초콜렛이 적합)
  * 가능한 한글 발음을 다수 생성 (RAINBOW -> 레인보, 레인보우, 렌보, 렌보우)
 
2. 참조
  * CMU Dictionary - <http://www.speech.cs.cmu.edu/cgi-bin/cmudict>

3. 사용
  ```
  import CMUToKorean
  
  result = CMUToKorean.convert(u'MIDDLE', u'M IH1 D AH0 L')
  
  for v in result:
    print v
    >>> 미덜
    >>> 미델
    >>> 미들
  ```
