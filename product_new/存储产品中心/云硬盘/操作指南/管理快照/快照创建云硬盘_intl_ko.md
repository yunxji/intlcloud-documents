## 작업 시나리오
스냅샷은 데이터를 공유하고 마이그레이션하는 중요한 방법입니다. 스냅샷에서 생성된 Cloud Block Storage（CBS）에는 스냅샷의 모든 데이터가 포함되며, 스냅샷을 생성해 스냅샷 용량과 같거나 큰 CBS에 스냅샷 생성을 사용할 수 있습니다.
- 스냅샷을 사용해 동일한 크기의 데이터 디스크를 추가할 경우, 새 데이터 디스크를 초기화할 필요가 없으며 클라우드 서버에 직접적으로 [마운트](https://intl.cloud.tencent.com/zh/document/product/362/32401) 후 즉시 정상적인 판독이 가능합니다.
- 스냅샷을 사용해 스냅샷보다 용량이 큰 데이터 디스크를 추가할 경우, 시스템은 블록 디바이스 레벨의 디스크 확장만 완료하며 파일 시스템의 확장 또는 파티션 형식의 자동 변환을 실현하지 않습니다. 새로운 데이터 디스크 [마운트](https://intl.cloud.tencent.com/zh/document/product/362/32401) 후에는 소스 스냅샷의 파일 시스템과 데이터만 사용할 수 있으며, 새 디스크 용량을 직접 사용할 수 없습니다. 파일 시스템을 수동으로 확장해야 하거나 파티션 형식을 변환해야 합니다.
  예를 들어, 1TB 용량을 가진 MBR 파티션 형식의 데이터 디스크 스냅샷으로 3TB 데이터 디스크를 추가할 경우, MBR이 지원하는 최대 디스크 용량은 2TB이므로 데이터 디스크를 포맷해야 하며 GPT를 사용해 다시 파티션 해야 합니다. 이러한 작업으로 **원본 데이터는 삭제됩니다.** 그러므로 **실제 필요도에 따라 신중히 작업하십시오.**

본 문서는 [스냅샷 리스트](https://console.cloud.tencent.com/cvm/snapshot) 페이지의 스냅샷을 통한 CBS 생성에 대해 안내합니다. 이 외에도, [CBS 생성](https://intl.cloud.tencent.com/document/product/362/5744)의 경우, 파라미터 구성을 통한 [스냅샷]과 상응하는 스냅샷으로 CBS를 생성할 수 있습니다.


## 작업 순서
### 콘솔을 이용해 스냅샷으로 CBS를 생성하는 경우
1. [스냅샷 리스트](https://console.cloud.tencent.com/cvm/snapshot) 페이지에 로그인하십시오.
2. 해당 스냅샷이 있는 라인에서 [더보기]를 클릭 후 [새 CBS 생성]를 선택하십시오.
3. [데이터 디스크 구매] 대화 상자에서 파라미터를 설정하십시오.
<table>
     <tr>
         <th width="12%">파라미터 항목</th>  
         <th>파라미터 설명</th>  
     </tr>
	<tr>
         <td>가용존</td>
         <td>필수 파라미터</br>CBS가 있는 가용존에서, CBS 생성 후 수정할 수 없습니다.</td>
     </tr>
     <tr>
         <td>CBS 유형</td>
         <td>필수 파라미터</br>CBS 유형은 다음을 포함합니다.<ul><li> 일반 CBS </li><li>프리미엄 CBS </li><li> SSD CBS</li></ul></td>
     </tr>
     <tr>
         <td>용량</td>
         <td>필수 파라미터</br>CBS의 용량, 규격 크기는 다음과 같습니다.<ul><li>일반 CBS: 10GB-16,000GB </li><li> 프리미엄 CBS: 50GB-16,000GB </li><li> SSD CBS: 100GB-16,000GB </li></ul>스냅샷을 통해 CBS를 생성할 경우, 용량 크기는 스냅샷 크기보다 작을 수 없습니다. CBS의 용량을 지정하지 않을 경우, 용량의 기본 크기는 스냅샷과 일치하도록 합니다.</td>
     </tr>
     <tr>
         <td>디스크 명칭</td>
         <td>선택 파라미터</br>최대 20자까지 지원하며, 대소문자 혹은 중국어를 시작으로 대소문자, 중국어, 숫자 및 ._ :-와 같은 특수 기호로 구성될 수 있습니다.  CBS 생성 완료 후 수정을 허용합니다. <ul><li> 개별 CBS 생성: 디스크 명칭은 CBS의 명칭입니다. </li><li> 일괄 CBS 생성: 한 번에 여러 개의 CBS를 생성할 경우, 디스크 명칭은 CBS 명칭의 접두사이며 최종 CBS 명칭은 "디스크 명칭_0"-"디스크 명칭_49" 사이의 [디스크 명칭_숫자]로 구성됩니다. </li></ul></li></ul></td>
     </tr>
	 <tr>
         <td>세부 항목</td>
         <td>필수 파라미터</br>CBS를 생성할 경우, CBS용 세부 항목을 설정할 수 있습니다. 기본값으로 작성되는 항목은 [기본 항목]입니다.</td>
     </tr>
	 <tr>
         <td>태그</td>
         <td>선택 파라미터</br>CBS를 생성할 경우, CBS에 태그를 추가할 수 있습니다. 태그는 클라우드 리소스 표시에 사용되며, 태그를 통해 클라우드 리소스의 분류와 검색이 실현될 수 있습니다. 태그에 대한 더 자세한 정보는 <a href="https://intl.cloud.tencent.com/document/product/651">태그 제품문서</a>를 참조하십시오.</td>
     </tr>
	 <tr>
         <td>청구 모드</td>
         <td>필수 파라미터</br>CBS가 지원하는 청구 모드 유형은 종량제입니다.
     </tr>
	 <tr>
	 	 <tr>
         <td>정기 백업</td>
         <td>선택 파라미터</br>CBS를 생성할 경우, 정기적 백업을 선택할 수 있으며, 생성된 정기적인 스냅샷 정책에 따라 CBS의 스냅샷을 정기적으로 생성할 수 있습니다. 정기적 백업에 대한 더 자세한 정보는 <a href="https://intl.cloud.tencent.com/document/product/362/31622">정기적 스냅샷</a>을 참조하십시오.
     </tr>
	 <tr>
         <td>구매 수량</td>
         <td>선택 파라미터</br>기본 수량은 [1]로 CBS를 1개만 생성할 수 있다는 것을 의미합니다. 현재 최대 CBS를 50개 일괄 생성할 수 있습니다.</td>
     </tr>
	 <tr>
         <td>구매 기간</td>
     <td><ul>만약 [청구 모드]에서 [종량제]를 선택한 경우 해당 파라미터와 연관되지 않습니다.</ul></td>
     </tr>
         <td>연장 갱신</td>
     <td><ul>만약 [청구 모드]에서 [종량제]를 선택한 경우 해당 파라미터와 연관되지 않습니다.</ul></td>
     </tr>
</table>

4. [확인]을 클릭하십시오.
 - 만약 [청구 모드]에서 [종량제]를 선택한 경우 추가가 완료됩니다.
 - 만약 [청구 모드]에서 [정액 요금제]를 선택한 경우 [정보 확인] 페이지로 진입합니다.
  <ol>
  1. 규격을 확인한 후 실제 상황에 따라 바우처 사용 여부를 선택하고 [구매 확인]을 클릭하십시오.
  2. 결제를 완료하십시오.
 </ol>
5. [CBS 리스트](https://console.cloud.tencent.com/cvm/cbs) 페이지에서 생성된 CBS를 확인할 수 있습니다. 새로 추가된 엘라스틱 CBS는 [마운트 대기] 상태입니다. 동일 가용존의 클라우드 서버에 CBS를 마운트하고 싶은 경우에는 [CBS 마운트](https://intl.cloud.tencent.com/zh/document/product/362/32401)를 참조하십시오.

###  API를 이용해 스냅샷으로 CBS를 생성하는 경우
CreateDisks 인터페이스를 사용해 스냅샷을 생성할 수 있습니다. 자세한 내용은 [CBS 생성](https://intl.cloud.tencent.com/document/product/362/16312)을 참조하십시오.
