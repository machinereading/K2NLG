# K2NLG

## Introduction
K2NLG란, 지식 집합(또는 지식 그래프)으로부터 요약문을 생성하는 태스크입니다. 모델의 대상 지식의 개체 타입과 관계는 KBox 온톨로지를 따르고, 이 코드는 [GraphWriter](https://github.com/rikdz/GraphWriter)를 기반으로 작성되었습니다.

## How to Use
For Training:
	
	python train.py -save <DIR> -epoch 50 -outunk 5 -entunk 1 -gpu 0 
	
For Generating:

	python generator.py -datadir ./data/ -data train.tsv -save <SAVED MODEL> -outunk 5 -entunk 1

For Evaluating:

	python eval.py <GENERATED TEXTS> <GOLD TARGETS>
	
## Data Example

	title	잉글랜드 ; 프랑스군 ; 대주교 ; 교황 ; 존	<Settlement> <MilitaryUnit> <Profession> <ChristianBishop> <BritishRoyalty>	4 106 0 ; 1 14 0 ; 4 11 3 ; 4 11 2 ; 0 26 4 ; 2 96 3	<ENTITY_4> 은 <ENTITY_0> 에서 사망하였다 . <ENTITY_4> 의 직업은 <ENTITY_3> 이다 . 그는 <ENTITY_2> 이다 . 그는 <ENTITY_0>  지도자이다 .	존 은 잉글랜드 에서 사망하였다 . 존 의 직업은 교황 이다 . 그는 대주교 이다 . 그는  잉글랜드 지도자이다 .	T ; F ; T ; T ; T ; F
	
Tsv format: title, entities, entity types, triples, masked sentences, sentences, selected triples  
### Triples
* A triple is composed of subject, property, object.   
* subject and object are index of entities.  
* property is index of each property in relations.vocab

## Output Example

	교황_하드리아노_4세 ; 시칠리아 ; 독일 ; 교황	(시칠리아, country, 독일) ; (교황_하드리아노_4세, position, 교황) ; (교황, leaderName, 교황_하드리아노_4세)	T ; F ; T	<entity_1> 를 이끄는 사람은 <entity_0> 다 . 그의 직함은 <entity_3> 이다 .	시칠리아 를 이끄는 사람은 교황_하드리아노_4세 다 . 그의 직함은 교황 이다 .
	
* For each instances, output is composed of entities, triples, triple selection, generated masked sentences, and generated unmasked sentences.

## Licenses
* `CC BY-NC-SA` [Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/2.0/)
* If you want to commercialize this resource, [please contact to us](http://semanticweb.kaist.ac.kr/)

## Publisher
[Machine Reading Lab](http://semanticweb.kaist.ac.kr/) @ KAIST

## Acknowledgement
This work was supported by Institute for Information & communications Technology Promotion(IITP) grant funded by the Korea government(MSIT) (2013-0-00109, WiseKB: Big data based self-evolving knowledge base and reasoning platform)
