# Index (/tds-mobile/)

## TDS를 소개해요

![Image](https://static.toss.im/3d-common/tds-kv-no-text-hero.png)

TDS는 토스 제품을 만들 때 공통적으로 사용하는 디자인 시스템이에요. 수백 개의 컴포넌트와 템플릿으로 구성되어 있고, 단순히 디자인 툴에만 머무는 것이 아니라 개발과 연결되어 토스 제품을 구성하는 하나의 언어처럼 사용돼요.

### TDS가 지향하는 목표

- 제품의 최소 품질을 언제나 보장해요. TDS를 사용하면 토스의 일관된 UI를 유지할 수 있기 때문이에요.
- 생산성을 향상시키고 문제 해결에 집중할 수 있도록 도와줘요. 재사용 할 수 있는 아름다운 디자인 시스템으로 제품의 UI 개발 과정을 효율적으로 만들어요.
- 일관성 있는 인터랙션, 애니메이션, 일러스트레이션, 디자인 템플릿을 통해 제품 완성도를 업계 최고 수준으로 끌어올리는 것이 최종 목표에요.

---

# AgreementV3 (/tds-mobile/components/Agreement/v3/)

# AgreementV3

> `AgreementV3`는 더 이상 사용되지 않아요. `AgreementV4`를 이용해 주세요.

`AgreementV3` 컴포넌트는 사용자의 동의를 받아야 하는 화면을 구성하기 위해 사용해요.
하지만 이 컴포넌트는 더 이상 유지보수되지 않으며, 최신 요구 사항을 반영한 `AgreementV4`가 역할을 대신해요.

[Preview: Basic]

## 사용법

### 체크박스 없이 정보만 표시하는 항목

`AgreementV3.SingleField` 컴포넌트는 체크박스 없이 정보를 표시하는 단순한 동의 항목을 생성하는 컴포넌트예요.  
추가 정보를 안내하거나, 약관 세부 내용으로 연결되는 링크에 주로 사용돼요.

**Example: SingleField**

```tsx
<div>
  <AgreementV3.SingleField type="medium-bold" arrowType="collapsible">
    이용약관
  </AgreementV3.SingleField>
  <AgreementV3.SingleField type="medium" arrowType="link">
    이용약관
  </AgreementV3.SingleField>
</div>
```

### 체크박스를 포함한 동의 항목

`AgreementV3.SingleCheckboxField` 컴포넌트는 체크박스를 포함한 동의 항목을 생성하는 컴포넌트예요.
`necessity` 속성을 통해 필수 항목인지 선택 항목인지 구분할 수 있어요.

- `none`: 항목에 필수나 선택 표시가 없어요.
- `mandatory`: [필수] 라벨이 추가되며, 반드시 동의해야 하는 항목이에요.
- `optional`: [선택] 라벨이 추가되며, 사용자가 선택적으로 동의할 수 있는 항목이에요.

**Example: SingleCheckboxField**

```tsx
<div>
  <AgreementV3.SingleCheckboxField type="medium">
    카드의 실제 소유자입니다
  </AgreementV3.SingleCheckboxField>
  <AgreementV3.SingleCheckboxField
    type="medium"
    arrowType="link"
    necessity="mandatory"
  >
    카드의 실제 소유자입니다
  </AgreementV3.SingleCheckboxField>
  <AgreementV3.SingleCheckboxField
    type="medium"
    arrowType="collapsible"
    necessity="optional"
  >
    카드의 실제 소유자입니다
  </AgreementV3.SingleCheckboxField>
</div>
```

### 여러 동의 항목을 그룹화하기

`AgreementV3.Group` 컴포넌트는 여러 동의 항목을 하나의 그룹으로 묶어주는 컴포넌트예요.
여러 항목을 논리적으로 구분하거나, 화면을 정리된 형태로 구성하고 싶을 때 유용해요.
그룹 안의 각각의 항목은 `AgreementV3.GroupItem`으로 생성하며, 항목이 많은 경우에도 시각적으로 깔끔하게 정리할 수 있어요.

이 컴포넌트는 여러 동의 항목을 가로로 정렬하며, 화면 너비가 좁아지거나 항목이 많아질 때는 자동으로 다음 줄로 넘어가요. 이를 통해 다양한 디바이스에서 일관된 사용자 경험을 제공할 수 있어요.

**Example: Group**

```tsx
<AgreementV3.Group indent={1}>
  <AgreementV3.GroupItem type="medium">동의합니다.</AgreementV3.GroupItem>
  <AgreementV3.GroupItem type="medium">동의합니다.</AgreementV3.GroupItem>
</AgreementV3.Group>
```

### 접었다 펼치는 동의 항목

`AgreementV3.CollapsibleGroup` 컴포넌트와 `AgreementV3.Collapsible` 컴포넌트는 긴 내용을 깔끔하게 정리하고 필요할 때만 내용을 펼쳐 볼 수 있도록 도와줘요.
약관이나 정책 설명이 길거나 동의 항목이 많아 화면이 복잡해질 우려가 있을 때 특히 유용해요.
이 기능은 기본 정보만 노출하고, 추가 내용은 사용자가 필요할 때 열람할 수 있도록 만들어 사용자 경험을 개선해요.

구현 방식은 `AgreementV3.CollapsibleGroup` 컴포넌트로 전체 영역을 감싸고, 실제로 접히고 펼쳐질 내용은 `AgreementV3.Collapsible` 컴포넌트로 구성해요.
안쪽에 `SingleCheckboxField`, `Group`과 같은 다른 컴포넌트를 자유롭게 중첩할 수 있어 다양한 형태의 동의 화면을 만들 수 있어요.
들여쓰기가 필요한 경우 각 컴포넌트의 `indent` 속성을 사용해서 시각적으로 구분할 수 있어요.

**Example: CollapsibleGroup**

```tsx
<div>
  <AgreementV3.CollapsibleGroup defaultOpen={true}>
    <AgreementV3.SingleField type="medium" arrowType="collapsible">
      개인정보 수집 동의
    </AgreementV3.SingleField>

    <AgreementV3.Collapsible>
      <AgreementV3.SingleCheckboxField
        indent={1}
        type="medium"
        necessity="mandatory"
      >
        동의해요 1-1
      </AgreementV3.SingleCheckboxField>
      <AgreementV3.SingleCheckboxField
        indent={1}
        type="medium"
        necessity="mandatory"
      >
        동의해요 1-2
      </AgreementV3.SingleCheckboxField>
      <AgreementV3.CollapsibleGroup defaultOpen={true}>
        <AgreementV3.SingleField
          indent={3}
          type="medium"
          arrowType="collapsible"
        >
          개인정보 수집 동의 group
        </AgreementV3.SingleField>
        <AgreementV3.Collapsible>
          <AgreementV3.Group indent={3}>
            <AgreementV3.GroupItem type="medium">
              동의해요 group item
            </AgreementV3.GroupItem>
            <AgreementV3.GroupItem type="medium">
              동의해요 group item
            </AgreementV3.GroupItem>
            <AgreementV3.GroupItem type="medium">
              동의해요 group item
            </AgreementV3.GroupItem>
          </AgreementV3.Group>
        </AgreementV3.Collapsible>
      </AgreementV3.CollapsibleGroup>
    </AgreementV3.Collapsible>
  </AgreementV3.CollapsibleGroup>
</div>
```

### 체크박스 버튼

`AgreementV3.Button` 컴포넌트는 전체 동의 기능을 제공하는 컴포넌트예요.
여러 동의 항목을 한 번에 모두 동의할 수 있는 버튼 형태의 UI를 제공해요.
체크박스를 포함하고 있어 사용자가 전체 동의를 클릭하면 시각적으로도 동의 상태를 확인할 수 있어요.

**Example: Button**

```tsx
<AgreementV3.Button
  inputType="checkbox"
  onCheckedChange={(checked) => console.log("전체 동의:", checked)}
>
  전체 동의하기
</AgreementV3.Button>
```

### 동의 항목 설명

`AgreementV3.Description` 컴포넌트는 동의 항목에 대한 부가 정보를 제공할 때 사용하는 컴포넌트예요.
작은 회색 글씨로 표시되며, 약관 세부 내용이나 참고 정보를 보여줄 때 적합해요.

**Example: Description**

```tsx
<div>
  <AgreementV3.SingleCheckboxField type="medium">
    개인정보 수집 및 이용 동의
  </AgreementV3.SingleCheckboxField>
  <AgreementV3.Description indent={1}>
    수집된 개인정보는 서비스 제공 목적으로만 사용됩니다.
  </AgreementV3.Description>
</div>
```

### 태그를 활용한 강조 표시

`AgreementV3.Tag` 컴포넌트는 동의 항목에 중요한 정보를 강조하거나 추가적인 메시지를 전달할 때 사용해요. 주요 키워드를 사용자가 빠르게 인식할 수 있도록 돕는 역할을 해요.

**Example: Tag**

```tsx
<AgreementV3.SingleCheckboxField
  type="medium"
  rightAddon={<AgreementV3.Tag color="#3182f6">안심</AgreementV3.Tag>}
>
  개인정보 수집 및 이용 동의
</AgreementV3.SingleCheckboxField>
```

## 상호작용하기

`AgreementV3` 컴포넌트는 다양한 상호작용 이벤트를 제공하며, 주로 `AgreementSingleField`, `AgreementSingleCheckboxField`, 그리고 `AgreementGroupItem`에서 활용돼요.

이 컴포넌트들은 `arrowType` 속성을 사용하여 링크 이동이나 접기/펼치기 기능을 제공해요.
각 이벤트는 특정 상황에서 사용되며, 아래 표는 주요 이벤트와 그 사용 조건을 설명해요.

| 이벤트 이름       | 설명                                                | `arrowType`이 `none`일 때 | `arrowType`이 `none`이 아닐 때                  |
| ----------------- | --------------------------------------------------- | ------------------------- | ----------------------------------------------- |
| `onClick`         | 사용자가 컴포넌트의 주요 영역을 클릭할 때 실행돼요. | 전체 영역에서 사용돼요.   | Link, Collapse Area를 제외한 영역에서 사용돼요. |
| `onPressEnd`      | 사용자가 터치 영역을 눌렀다가 뗄 때 실행돼요.       | 전체 영역에서 사용돼요.   | Link, Collapse Area를 제외한 영역에서 사용돼요. |
| `onArrowClick`    | 화살표 아이콘을 클릭할 때 실행돼요.                 | 사용되지 않아요.          | Link, Collapse Area에서 사용돼요.               |
| `onArrowPressEnd` | 화살표 아이콘을 터치했다가 뗄 때 실행돼요.          | 사용되지 않아요.          | Link, Collapse Area에서 사용돼요.               |

체크 상태 변경 이벤트는 `AgreementV3.SingleCheckboxField`에서 `onCheckedChange`로, `AgreementV3.GroupItem`에서 `onChange`로 사용돼요.
이러한 이벤트를 적절히 활용하여 `AgreementV3` 컴포넌트의 상호작용을 더욱 풍부하게 만들 수 있어요.

**Example: AgreementEventExample**

```tsx
function AgreementEventExample() {
  const handleCheckedChange = (checked: boolean) => {
    console.log("Checkbox checked state:", checked);
  };

  const handleChange = (event: React.ChangeEvent<HTMLInputElement>) => {
    console.log("Group item state changed:", event.target.checked);
  };

  const handleClick = () => {
    console.log("Main area clicked");
  };

  const handleArrowClick = () => {
    console.log("Arrow clicked");
  };

  return (
    <div>
      <AgreementV3.SingleCheckboxField
        type="medium"
        arrowType="link"
        onCheckedChange={handleCheckedChange}
        onClick={handleClick}
        onArrowClick={handleArrowClick}
      >
        Single Checkbox Field
      </AgreementV3.SingleCheckboxField>
      <AgreementV3.Group>
        <AgreementV3.GroupItem
          type="medium"
          arrowType="collapsible"
          onChange={handleChange}
          onClick={handleClick}
          onArrowClick={handleArrowClick}
        >
          Group Item
        </AgreementV3.GroupItem>
        <AgreementV3.GroupItem
          type="medium"
          arrowType="link"
          onChange={handleChange}
          onClick={handleClick}
          onArrowClick={handleArrowClick}
        >
          Group Item
        </AgreementV3.GroupItem>
      </AgreementV3.Group>
    </div>
  );
}
```

## 인터페이스

**Type: AgreementSingleFieldProps**

```typescript
export interface AgreementSingleFieldProps {
  /**
   * 동의 항목의 크기와 스타일을 설정해요.
   *
   * - `medium`: 기본 크기에요.
   * - `medium-bold`: 굵은 텍스트를 사용해요.
   * - `big`: 더 큰 크기에요.
   */
  type: "big" | "medium" | "medium-bold";
  /**
   * 동의 항목 옆에 배치할 화살표 형태를 설정해요.
   *
   * - `none`: 화살표가 없어요.
   * - `link`: 링크 형태의 화살표에요.
   * - `collapsible`: 펼치기/접기 형태의 화살표에요.
   *
   * @default none
   */
  arrowType?: "none" | "link" | "collapsible";
  /**
   * 동의 항목 아래에 구분선을 표시해요.
   *
   * @default false
   */
  withBorder?: boolean;
  /**
   * 동의 항목의 동의 항목의 들여쓰기 값을 설정해요.
   * @default 0
   */
  indent?: number;
  /**
   * 동의 항목의 펼침 상태를 설정해요.
   * `arrowType`이 `collapsible`일 때만 사용돼요.
   * @default false
   */
  open?: boolean;
  /**
   * 동의 항목 오른쪽에 추가할 수 있는 컴포넌트예요.
   */
  rightAddon?: React.ReactNode;
  /**
   * 동의 항목의 내용이에요.
   */
  children?: string;
  /**
   * `Link`, `Collapse` 영역을 제외한 모든 터치영역을 클릭했을 때 실행되는 콜백이에요.
   */
  onClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  /**
   * `Link`, `Collapse` 영역을 클릭했을 때 실행되는 콜백이에요.
   * `arrowType`이 none이 아닐 경우 실행돼요.
   */
  onArrowClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  /**
   * `Link`, `Collapse` 영역을 제외한 영역의 터치가 끝날 때 실행되는 콜백이에요.
   */
  onPressEnd?: () => void;
  /**
   * `Link`, `Collapse` 영역의 터치가 끝날 때 실행되는 콜백이에요.
   * `arrowType`이 `none`이 아닐 경우 실행돼요.
   */
  onArrowPressEnd?: () => void;
}
```

**Type: AgreementSingleCheckboxFieldProps**

```typescript
export interface AgreementSingleCheckboxFieldProps {
  /**
   * 동의 항목의 크기와 스타일을 설정해요.
   *
   * - `medium`: 기본 크기에요.
   * - `medium-bold`: 굵은 텍스트를 사용해요.
   * - `big`: 더 큰 크기에요.
   */
  type?: "big" | "medium" | "medium-bold";
  /**
   * 동의 항목 옆에 배치할 화살표 형태를 설정해요.
   *
   * - `none`: 화살표가 없어요.
   * - `link`: 링크 형태의 화살표에요.
   * - `collapsible`: 펼치기/접기 형태의 화살표에요.
   *
   * @default none
   */
  arrowType?: "none" | "link" | "collapsible";
  /**
   * 동의 항목 아래에 구분선을 표시해요.
   */
  withBorder?: boolean;
  /**
   * 동의 항목의 체크 상태를 설정해요.
   * controlled로 외부에서 상태를 제어할 수 있어요.
   */
  checked?: boolean;
  /**
   * 동의 항목의 필수 여부를 설정해요.
   *
   * - `none`: 필수가 아니에요.
   * - `optional`: 선택이 가능해요.
   * - `mandatory`: 필수에요.
   *
   * @default none
   */
  necessity?: "none" | "optional" | "mandatory";
  /**
   * 동의 항목의 들여쓰기 값을 설정해요.
   * @default 0
   */
  indent?: number;
  /**
   * 동의 항목의 펼침 상태를 설정해요.
   * `arrowType`이 `collapsible`일 때만 사용돼요.
   * @default false
   */
  open?: boolean;
  /**
   * 동의 항목 오른쪽에 추가할 수 있는 컴포넌트예요.
   */
  rightAddon?: React.ReactNode;
  /**
   * 동의 항목의 내용이에요.
   */
  children?: string;
  /**
   * 동의 항목의 체크 상태가 변경될 때 호출되는 함수에요.
   */
  onCheckedChange?: (checked: boolean) => void;
  /**
   * `Link`, `Collapse` 영역을 제외한 모든 터치영역을 클릭했을 때 실행되는 콜백이에요.
   */
  onClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  /**
   * `Link`, `Collapse` 영역의 화살표를 클릭했을 때 실행되는 콜백이에요.
   * `arrowType`이 `none`이 아닐 경우 실행돼요.
   */
  onArrowClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  /**
   * `Link`, `Collapse` 영역을 제외한 영역의 터치가 끝날 때 실행되는 콜백이에요.
   */
  onPressEnd?: () => void;
  /**
   * `Link`, `Collapse` 영역의 터치가 끝날 때 실행되는 콜백이에요.
   * `arrowType`이 `none`이 아닐 경우 실행돼요.
   */
  onArrowPressEnd?: () => void;
}
```

**Type: AgreementGroupProps**

```typescript
export interface AgreementGroupProps {
  /**
   * 동의 항목의 들여쓰기 값을 설정해요.
   * @default 0
   */
  indent?: number;
  /**
   * 그룹 내부에 들어갈 컴포넌트들이에요.
   * 주로 `GroupItem` 컴포넌트와 함께 사용돼요.
   */
  children: React.ReactNode;
}
```

**Type: AgreementGroupItemProps**

```typescript
export interface AgreementGroupItemProps {
  /**
   * 동의 항목의 크기와 스타일을 설정해요.
   *
   * - `medium`: 기본 크기에요.
   * - `medium-bold`: 굵은 텍스트를 사용해요.
   * - `big`: 더 큰 크기에요.
   */
  type: "big" | "medium" | "medium-bold";
  /**
   * 동의 항목 옆에 배치할 화살표 형태를 설정해요.
   *
   * - `none`: 화살표가 없어요.
   * - `link`: 링크 형태의 화살표에요.
   * - `collapsible`: 펼치기/접기 형태의 화살표에요.
   *
   * @default none
   */
  arrowType?: "none" | "link" | "collapsible";
  /**
   * 체크 상태를 설정해요.
   * controlled로 외부에서 상태를 제어할 수 있어요.
   */
  checked?: boolean;
  /**
   * 동의 항목의 펼침 상태를 설정해요.
   * `arrowType`이 `collapsible`일 때만 사용돼요.
   * @default false
   */
  open?: boolean;
  /**
   * 동의 항목의 오른쪽에 추가할 수 있는 컴포넌트예요.
   */
  rightAddon?: React.ReactNode;
  /**
   * 동의 항목의 내용이에요.
   */
  children?: string;
  /**
   * 동의 항목의 체크 상태가 변경될 때 호출되는 함수에요.
   */
  onChange?: (event: React.ChangeEvent<HTMLInputElement>) => void;
  /**
   * `Link`, `Collapse` 영역을 제외한 모든 터치영역을 클릭했을 때 실행되는 콜백이에요.
   */
  onClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  /**
   * `Link`, `Collapse` 영역의 화살표를 클릭했을 때 실행되는 콜백이에요.
   * `arrowType`이 `none`이 아닐 경우 실행돼요.
   */
  onArrowClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  /**
   * `Link`, `Collapse` 영역을 제외한 영역의 터치가 끝날 때 실행되는 콜백이에요.
   */
  onPressEnd?: () => void;
  /**
   * `Link`, `Collapse` 영역의 터치가 끝날 때 실행되는 콜백이에요.
   * `arrowType`이 `none`이 아닐 경우 실행돼요.
   */
  onArrowPressEnd?: () => void;
}
```

**Type: AgreementCollapsibleGroupProps**

```typescript
export interface AgreementCollapsibleGroupProps {
  /**
   * `CollapsibleGroup` 컴포넌트의 펼침 상태를 설정해요.
   * controlled로 외부에서 상태를 제어할 수 있어요.
   */
  open?: boolean;
  /**
   * `CollapsibleGroup` 컴포넌트의 초기 펼침 상태를 설정해요.
   * uncontrolled로 사용할 때 초기값을 설정할 수 있어요.
   */
  defaultOpen?: boolean;
  /**
   * `CollapsibleGroup` 컴포넌트 내부에 들어갈 컴포넌트들이에요.
   * 주로 `SingleField`, `SingleCheckboxField`, `Collapsible` 컴포넌트들과 함께 사용돼요.
   */
  children?: React.ReactNode;
  /**
   * `CollapsibleGroup` 컴포넌트의 펼침 상태가 변경될 때 호출되는 함수에요.
   */
  onChange?: (open: boolean) => void;
}
```

**Type: AgreementCollapsibleProps**

```typescript
export interface AgreementCollapsibleProps {
  /**
   * `Collapsible` 컴포넌트의 펼침/접힘 상태를 제어해요.
   */
  open?: boolean;
  /**
   * `Collapsible` 컴포넌트 내부에 들어갈 컴포넌트들이에요.
   * 주로 `SingleField`, `SingleCheckboxField`, `Group` 컴포넌트들과 함께 사용돼요.
   */
  children?: React.ReactNode;
}
```

**Type: AgreementButtonProps**

```typescript
export interface AgreementButtonProps {
  /**
   * input 태그의 `type` 속성을 설정해요.
   * @default 'checkbox'
   * @note radio는 아직 지원하지 않아요.
   */
  inputType?: "checkbox" | "radio";
  /**
   * `Checkbox` 컴포넌트의 크기를 설정해요.
   * @default 24
   */
  size?: number;
  /**
   * 버튼 내용으로 들어갈 컴포넌트들이에요.
   */
  children: React.ReactNode;
  /**
   * `Checkbox` 컴포넌트의 선택 상태가 바뀔 때 실행되는 함수예요.
   */
  onCheckedChange?(checked: boolean): void;
}
```

**Type: AgreementDescriptionProps**

```typescript
export interface AgreementDescriptionProps {
  /**
   * 설명의 들여쓰기 값을 설정해요.
   * @default 0
   */
  indent?: number;
  /**
   * 설명 내용으로 들어갈 컴포넌트들이에요.
   */
  children?: React.ReactNode;
}
```

**Type: AgreementTagProps**

```typescript
export interface AgreementTagProps {
  /**
   * 태그의 텍스트 색상을 설정해요.
   */
  color?: string;
  /**
   * 태그 내용으로 들어갈 컴포넌트들이에요.
   */
  children: React.ReactNode;
}
```

---

# AgreementV4 (/tds-mobile/components/Agreement/v4/)

# AgreementV4

`AgreementV4` 컴포넌트는 사용자의 동의를 받아야 하는 화면을 간편하게 구성할 수 있도록 도와줘요. 여러 동의 항목을 쉽게 추가할 수 있고, 항목을 그룹화하거나 접고 펼치는 기능을 활용해 UI를 깔끔하게 정리할 수 있어요. 또, 체크박스, 설명글, 태그 등 다양한 구성 요소를 지원해서 동의받을 내용을 유저에게 잘 설명해 줄 수 있어요.

[Preview: Basic]

## AgreementV4 구성요소 활용법 알아보기

`AgreementV4` 컴포넌트는 동의 화면을 구성하는 데 필요한 다양한 하위 컴포넌트를 제공해요. 이 구성 요소들을 조합하면 사용자가 쉽게 이해할 수 있는 직관적이고 정리된 동의 화면을 만들 수 있어요.

### 텍스트 사용하기

`AgreementV4.Text`는 동의 항목의 설명이나 제목을 표시하는 텍스트 컴포넌트예요.
`onPressEnd` 속성과 함께 사용하면 사용자 클릭을 감지하여 인터랙션을 제공해 사용자에게 명확한 피드백을 제공해요.

**Example: Text**

```tsx
<div>
  <AgreementV4
    variant="large"
    middle={<AgreementV4.Text>텍스트</AgreementV4.Text>}
  />
  <AgreementV4
    variant="large"
    middle={
      <AgreementV4.Text onPressEnd={() => console.log("press")}>
        텍스트를 클릭해보세요.
      </AgreementV4.Text>
    }
  />
</div>
```

### 뱃지 사용하기

`AgreementV4.Badge`는 동의 항목에 시각적 강조를 추가하는 컴포넌트예요.
`variant`가 `fill`일 때 배경색을 지정할 수 있어요.

**Example: Badge**

```tsx
<div>
  <AgreementV4
    variant="large"
    middle={<AgreementV4.Text>서비스 이용 동의</AgreementV4.Text>}
    right={
      <AgreementV4.Badge
        variant="fill"
        bgColor={adaptive.yellow50}
        textColor={adaptive.yellow500}
      >
        배경 있음
      </AgreementV4.Badge>
    }
  />
  <AgreementV4
    variant="large"
    middle={<AgreementV4.Text>서비스 이용 동의</AgreementV4.Text>}
    right={
      <AgreementV4.Badge variant="clear" textColor={adaptive.blue500}>
        배경 없음
      </AgreementV4.Badge>
    }
  />
</div>
```

### 체크박스 사용하기

`AgreementV4.Checkbox`는 사용자의 선택을 받기 위한 체크박스 컴포넌트예요.
`variant`가 `'checkbox'`, `'dot'`, `'hidden'`이 있어서 상황에 맞게 사용할 수 있어요.
`hidden` 옵션은 체크박스를 시각적으로 숨기고 레이아웃만 유지할 때 유용해요. 체크박스는 보이지 않지만 공간은 그대로 차지해요.

**Example: Checkbox**

```tsx
<div>
  }
    middle={<AgreementV4.Text>checkbox</AgreementV4.Text>}
  />
  }
    middle={<AgreementV4.Text>dot</AgreementV4.Text>}
  />
  }
    middle={<AgreementV4.Text>hidden</AgreementV4.Text>}
  />
</div>
```

### 필수 여부 나타내기

`AgreementV4.Necessity`는 동의 항목의 필수 여부를 나타내는 컴포넌트예요. `variant`가 'optional', 'mandatory'가 있어서 상황에 따라 적용할 수 있으며, 색상이 다르게 표시돼요.
주로 `AgreementV4.Text`의 `necessity` 속성에서 사용돼요.
필수와 옵션 항목을 명확히 구분하면 사용자는 어떤 항목이 반드시 필요한지 명확히 알 수 있어, 동의 과정을 더 수월하게 진행할 수 있어요.

**Example: Necessity**

```tsx
<div>
  }
    middle={
      <AgreementV4.Text necessity={<AgreementV4.Necessity variant="mandatory">필수</AgreementV4.Necessity>}>
        서비스 이용 동의
      </AgreementV4.Text>
    }
  />
  }
    middle={
      <AgreementV4.Text necessity={<AgreementV4.Necessity variant="optional">선택</AgreementV4.Necessity>}>
        서비스 이용 동의
      </AgreementV4.Text>
    }
  />
</div>
```

### 접고 펼치기 화살표 사용하기

`AgreementV4.RightArrow`는 동의 항목을 접거나 펼치는 기능을 제공하는 화살표예요. 오른쪽에 있는 화살표로, 접기 화살표가 나와요. `collapsed` 컴포넌트에 트리거 용도로 사용돼요.

**Example: RightArrow**

```tsx
<AgreementV4
  variant="large"
  middle={<AgreementV4.Text>개인정보 수집 동의</AgreementV4.Text>}
  right={}
/>
```

### 설명 추가하기

`AgreementV4.Description`는 동의 항목에 대한 부가 정보를 제공할 때 사용하는 컴포넌트예요. 작은 회색 글씨로 표시되며, 약관 세부 내용이나 참고 정보를 보여줄 때 적합해요.
`variant` 속성을 통해 스타일을 조정할 수 있으며 이를 통해 설명의 가독성을 높이고, 시각적으로 구분할 수 있어요.

- `box`: 설명을 박스 형태로 감싸서 강조할 수 있어요. `box` 속성은 배경색과 패딩이 추가되어 설명을 시각적으로 구분하는 데 유용해요.
- `normal`: 기본 스타일로, 패딩 없이 간결하게 설명을 표시해요. `normal` 속성은 설명을 간단하게 표시하고 싶을 때 적합해요.

**Example: Description**

```tsx
<div>
  <AgreementV4.Description variant="box">
    수집된 개인정보는 서비스 제공 목적으로만 사용됩니다.
  </AgreementV4.Description>
  <AgreementV4.Description variant="normal">
    수집된 개인정보는 서비스 제공 목적으로만 사용됩니다.
  </AgreementV4.Description>
</div>
```

### 헤더 사용하기

`AgreementV4.Header`는 동의 항목의 제목이나 섹션을 시각적으로 구분하는 컴포넌트예요.
다양한 `variant` 옵션을 통해 크기와 스타일을 조절할 수 있어요.

**Example: Header**

```tsx
<div>
  <AgreementV4.Header variant="xLarge">Header</AgreementV4.Header>
  <AgreementV4.Header variant="medium" indent={1}>
    Header
  </AgreementV4.Header>
</div>
```

### 클릭 감지하기

`AgreementV4.Pressable`은 사용자의 클릭을 감지하여 인터랙션을 제공해 명확한 피드백을 제공해요. `onPressEnd`와 함께 사용해요.

**Example: Pressable**

```tsx
}
  middle={
    <AgreementV4.Pressable onPressEnd={() => console.log('press')}>
      <AgreementV4.Text necessity={<AgreementV4.Necessity variant="mandatory">필수</AgreementV4.Necessity>}>
        체크박스를 제외한 부분을 클릭해보세요.
      </AgreementV4.Text>
      <AgreementV4.Badge variant="clear" textColor={adaptive.blue500}>
        안심
      </AgreementV4.Badge>

    </AgreementV4.Pressable>
  }
/>
```

## 사용법

### 단일 동의 항목 생성하기

`AgreementV4` 컴포넌트는 단일 동의 항목을 생성하는 데 사용돼요.
`left`, `middle`, `right` 속성을 통해 체크박스, 텍스트, 추가 정보 등 다양한 컴포넌트를 사용하여 원하는 구성을 구현할 수 있어요.

- `left`: 주로 선택 요소를 배치하는 공간이에요. `AgreementV4.Checkbox`와 같은 컴포넌트가 주로 사용돼요.
- `middle`: 동의 항목의 제목이나 주요 텍스트를 표시하는 공간이에요. `AgreementV4.Text` 컴포넌트가 주로 사용돼요.
- `right`: 추가 정보나 인터랙션을 위한 요소를 배치하는 공간이에요. `AgreementV4.Badge` 또는 `AgreementV4.RightArrow` 컴포넌트가 주로 사용돼요.

**Example: AgreementV4Item**

```tsx
<div>
  }
    middle={<AgreementV4.Text>서비스 이용 동의</AgreementV4.Text>}
    right={
      <AgreementV4.Badge variant="fill" bgColor={adaptive.yellow50} textColor={adaptive.yellow500}>
        안심
      </AgreementV4.Badge>
    }
  />
  }
    middle={<AgreementV4.Text>서비스 이용 동의</AgreementV4.Text>}
    right={}
  />
  }
    middle={<AgreementV4.Text>서비스 이용 동의</AgreementV4.Text>}
  />
</div>
```

### 시각적 계층 구성하기

`AgreementV4.IndentPushable` 컴포넌트는 동의 항목의 시각적 계층을 명확히 할 때 유용해요.
주로 여러 단계의 동의 항목이 있을 때, 사용자가 각 항목의 관계를 명확히 이해할 수 있도록 할 때 사용돼요.
이 기능은 항목 간의 관계에 대한 이해도를 높여주어, 사용자 경험을 개선해요.

- `AgreementV4.IndentPushable`: 계층을 적용할 컴포넌트의 전체 영역을 감싸요.
- `AgreementV4.IndentPushableTrigger`: 클릭 시 내용을 들여쓰기 할 수 있는 트리거 컴포넌트예요.
- `AgreementV4.IndentPushableContent`: 트리거가 활성화되면 들여쓰기가 적용돼요.

`AgreementV4.IndentPushable` 컴포넌트는 `pushed` 속성을 통해 `AgreementV4.IndentPushableContent`의 들여쓰기를 제어할 수 있어요.
`pushed`가 `true`일 경우, `IndentPushableContent`에 포함된 약관들의 들여쓰기가 1만큼 증가해요.
하지만 약관 컴포넌트가 직접 가지는 `indent` 속성의 우선순위가 더 높기 때문에, 이 점을 고려하여 사용해야 해요.

**Example: IndentPushable**

```tsx
<>
  <AgreementV4.IndentPushable>
    <AgreementV4.IndentPushableTrigger>
      }
        middle={<AgreementV4.Text>카드상품 이외의 부수 서비스 안내 등을 위한 수집, 이용</AgreementV4.Text>}
        right={
          <AgreementV4.Badge variant="clear" textColor={adaptive.blue500}>
            안심
          </AgreementV4.Badge>
        }
      />
    </AgreementV4.IndentPushableTrigger>
    <AgreementV4.IndentPushableContent>
      }
        middle={<AgreementV4.Text>고유식별정보 수집/이용</AgreementV4.Text>}
      />
      }
        middle={<AgreementV4.Text>개인(신용)정보 수집/이용</AgreementV4.Text>}
      />
    </AgreementV4.IndentPushableContent>
  </AgreementV4.IndentPushable>
</>
```

### 접었다 펼치는 동의 항목 구현하기

`AgreementV4.Collapsible` 컴포넌트는 긴 내용을 깔끔하게 정리하고 필요할 때만 내용을 펼쳐 볼 수 있도록 도와줘요.
약관이나 정책 설명이 길거나 동의 항목이 많아 화면이 복잡해질 우려가 있을 때 특히 유용해요.
이 기능은 기본 정보만 노출하고, 추가 내용은 사용자가 필요할 때 열람할 수 있도록 만들어 사용자 경험을 개선해요.

- `AgreementV4.Collapsible`: 컴포넌트의 상태에 따라 내용을 접거나 펼칠 수 있는 기능을 제공해요. `collapsed` 속성을 통해 현재 상태를 제어하며, `onCollapsedChange` 이벤트를 통해 상태 변화를 처리할 수 있어요.
- `AgreementV4.CollapsibleTrigger`: 클릭 시 내용을 펼치거나 접을 수 있는 트리거 컴포넌트예요.
- `AgreementV4.CollapsibleContent`: 트리거가 활성화되면 표시되는 내용을 포함해요.

**Example: Collapsed**

```tsx
function Collapsed() {
  const [isOpen, setIsOpen] = React.useState(false);

  return (
    <AgreementV4.Collapsible collapsed={isOpen} onCollapsedChange={() => setIsOpen((prev) => !prev)}>
      <AgreementV4.CollapsibleTrigger>
        <AgreementV4
          variant="large"
          middle={<AgreementV4.Text>개인정보 수집 동의 (오른쪽 화살표를 클릭해보세요.)</AgreementV4.Text>}
          right={}
        />
      </AgreementV4.CollapsibleTrigger>
      <AgreementV4.CollapsibleContent>
        }
          middle={<AgreementV4.Text>동의해요</AgreementV4.Text>}
        />
        }
          middle={<AgreementV4.Text>동의해요</AgreementV4.Text>}
        />
      </AgreementV4.CollapsibleContent>
    </AgreementV4.Collapsible>
  );
}
```

### 여러 동의 항목 그룹화하기

`AgreementV4.Group` 컴포넌트는 여러 동의 항목을 하나의 그룹으로 묶어주는 컴포넌트예요.
이 컴포넌트는 여러 항목을 논리적으로 구분하여 사용자에게 일관된 정보를 제공하는 데 목적이 있어요.
또한, `showGradient` 속성을 통해 시각적 구분을 강화할 수 있어요. 이 속성은 기본적으로 활성화되어 있으며, 필요에 따라 비활성화하여 그라데이션 효과를 사용하지 않을 수도 있어요.

**Example: Group**

```tsx
<AgreementV4.Group>
  }
    middle={<AgreementV4.Text>카드상품 이외의 부수서비스 안내 등을 위한 수집/이용</AgreementV4.Text>}
  />
  }
    middle={<AgreementV4.Text>개인(신용)정보 수집/이용</AgreementV4.Text>}
  />
  }
    middle={<AgreementV4.Text>전자적 매체를 통한 광고성 정보 수신</AgreementV4.Text>}
  />
</AgreementV4.Group>
```

## 인터페이스

**Type: AgreementV4Props**

```typescript
export interface AgreementV4Props {
  /**
   * 동의 항목의 들여쓰기 정도를 설정해요.
   */
  indent?: number;
  /**
   * 동의 항목의 크기 및 스타일을 결정해요.
   *
   * - `xLarge`: 매우 큰 크기예요.
   * - `large`: 큰 크기예요.
   * - `medium`: 중간 크기예요.
   * - `medium-title`: 중간 크기의 제목 스타일이에요.
   * - `small`: 작은 크기예요.
   * - `small-last`: 마지막 작은 크기예요.
   */
  variant:
    "xLarge" | "large" | "medium" | "medium-title" | "small" | "small-last";
  /**
   * `AgreementV4` 컴포넌트의 왼쪽 영역에 들어갈 요소를 설정해요.
   */
  left?: React.ReactNode;
  /**
   * `AgreementV4` 컴포넌트의 중간에 들어갈 요소를 설정해요.
   */
  middle?: React.ReactNode;
  /**
   * `AgreementV4` 컴포넌트의 오른쪽에 들어갈 요소를 설정해요.
   */
  right?: React.ReactNode;
  /**
   * 동의 항목이 클릭되었을 때 호출되는 함수예요.
   */
  onPressEnd?: () => void;
}
```

**Type: AgreementV4BadgeProps**

```typescript
export interface AgreementV4BadgeProps {
  /**
   * 뱃지의 스타일을 결정해요.
   *
   * - `fill`: 배경색이 채워진 스타일이에요.
   * - `clear`: 투명한 스타일이에요.
   */
  variant: "fill" | "clear";
  /**
   * 텍스트 색상을 설정해요.
   */
  textColor: string;
  /**
   * 배경 색상을 설정해요.
   * `variant` 속성이 `fill`일 때는 `string`이 적용되고, 필수값이에요.
   * `variant` 속성이 `clear`일 때는 `unknown`이 적용되고, 선택적이에요.
   */
  bgColor?: "string | unknown";
}
```

**Type: AgreementV4CheckboxProps**

```typescript
export interface AgreementV4CheckboxProps {
  /**
   * 체크박스의 체크 상태를 제어하는 상태예요.
   * 이 속성을 사용하려면 `onCheckedChange`도 함께 전달해서 제어 컴포넌트로 설정해야 해요.
   */
  checked?: boolean;
  /**
   * 체크박스 모양을 정할 수 있어요.
   *
   * - `checkbox`: 기본 체크박스 모양이에요.
   * - `dot`: 점 모양의 체크박스에요.
   * - `hidden`: 체크박스를 노출하지 않아요.
   *
   * @default 'checkbox'
   */
  variant?: "checkbox" | "dot" | "hidden";
  /**
   * 체크박스가 체크/언체크될 때 모션의 형태를 정할 수 있어요.
   *
   * - `strong`: 바운스가 섞인 모션으로, 더 강한 시각적 효과를 줘요.
   * - `weak`: 기본 모션으로, 부드러운 시각적 효과를 줘요.
   *
   * @default 'weak'
   */
  motionVariant?: "strong" | "weak";
  /**
   * 체크박스가 체크되거나 해제될 때 모션의 시작 지연 시간을 설정해요.
   * 설정된 값에 0.1초가 자동으로 추가되어, 최종 지연 시간이 계산돼요.
   * 이 속성을 사용하면 체크박스 모션의 시작 타이밍을 조정할 수 있어요.
   *
   * 예를 들어, `transitionDelay`를 `0.2`로 설정하면, 실제 지연 시간은 `0.3초`가 돼요.
   *
   *
   * @default 0
   */
  transitionDelay?: number;
  /**
   * 체크박스의 체크 상태가 변경될 때 호출되는 콜백 함수에요.
   * `checked` 상태가 변경되면 이 함수가 호출되어, 외부에서 상태 변화를 감지할 수 있어요.
   */
  onCheckedChange?: (checked: boolean) => void;
}
```

**Type: AgreementV4TextProps**

```typescript
export interface AgreementV4TextProps {
  /**
   * 텍스트 앞에 표시할 추가적인 정보를 나타내는 요소에요.
   * 주로 `AgreementV4.Necessity` 컴포넌트를 사용해요.
   */
  necessity?: React.ReactNode;
  /**
   * 터치 이벤트가 끝날 때 호출되는 콜백 함수에요.
   * 사용자가 텍스트를 터치한 후 손을 뗄 때 실행할 동작을 정의할 수 있어요.
   */
  onPressEnd?: () => void;
}
```

**Type: AgreementV4NecessityProps**

```typescript
export interface AgreementV4NecessityProps {
  /**
   * 약관 필수 여부를 나타내는 속성이에요.
   *
   * - `optional`: 선택 사항을 나타내며, 진한 회색으로 표시돼요.
   * - `mandatory`: 필수 사항을 나타내며, 파란색으로 표시돼요.
   */
  variant: "optional" | "mandatory";
}
```

**Type: AgreementV4RightArrowProps**

```typescript
export interface AgreementV4RightArrowProps {
  /**
   * 화살표가 접혀 있는지 여부를 나타내는 속성이에요.
   * `true`일 때는 화살표가 접혀 있고, `false`일 때는 펼쳐져 있어요.
   */
  collapsed?: boolean;
  /**
   * 화살표를 클릭할 때 호출되는 콜백 함수에요.
   * 사용자가 화살표를 클릭하면 이 함수가 실행돼요.
   */
  onArrowClick?: () => void;
}
```

**Type: AgreementV4DescriptionProps**

```typescript
export interface AgreementV4DescriptionProps {
  /**
   * 약관 설명의 들여쓰기 정도를 설정해요.
   *
   * @default 0
   */
  indent?: number;
  /**
   * 약관 설명의 스타일을 설정해요.
   *
   * - `box`: 박스 형태로 설명을 표시해요.
   * - `normal`: 일반 텍스트 형태로 설명을 표시해요.
   */
  variant: "box" | "normal";
}
```

**Type: AgreementV4HeaderProps**

```typescript
export interface AgreementV4HeaderProps {
  /**
   * `Header` 컴포넌트의 들여쓰기 정도를 설정해요.
   *
   * @default 0
   */
  indent?: number;
  /**
   * `Header` 컴포넌트의 크기 및 스타일을 결정해요.
   *
   * - `xLarge`: 매우 큰 크기예요.
   * - `large`: 큰 크기예요.
   * - `medium`: 중간 크기예요.
   * - `medium-title`: 중간 크기의 제목 스타일이에요.
   * - `small`: 작은 크기예요.
   * - `small-last`: 마지막 작은 크기예요.
   */
  variant:
    "xLarge" | "large" | "medium" | "medium-title" | "small" | "small-last";
}
```

**Type: AgreementV4PressableProps**

```typescript
export interface AgreementV4PressableProps {
  /**
   * 터치 이벤트가 끝날 때 호출되는 콜백 함수에요.
   * 사용자가 텍스트를 터치한 후 손을 뗄 때 실행할 동작을 정의할 수 있어요.
   */
  onPressEnd?: () => void;
}
```

**Type: AgreementV4IndentPushableProps**

```typescript
export interface AgreementV4IndentPushableProps {
  /**
   * 들여쓰기 가능한 컴포넌트 내에 포함될 자식 요소들을 나타내요.
   */
  children: React.ReactNode;
  /**
   * `IndentPushable` 컴포넌트가 현재 들여쓰기 상태인지 여부를 나타내요.
   * `true`일 때는 들여쓰기가 적용되고, `false`일 때는 적용되지 않아요.
   * 이 속성을 사용하면 외부에서 들여쓰기 상태를 제어할 수 있어요.
   */
  pushed?: boolean;
  /**
   * `IndentPushable` 컴포넌트의 초기 들여쓰기 상태를 설정해요.
   * `true`일 때는 기본적으로 들여쓰기가 적용되어 있고, `false`일 때는 들여쓰기를 하지 않아요.
   */
  defaultPushed?: boolean;
  /**
   * 들여쓰기 상태가 변경될 때 호출되는 콜백 함수에요.
   * 상태가 변경되면 `pushed` 값이 인자로 전달돼요.
   * 이 함수를 사용하면 상태 변화를 감지하고 처리할 수 있어요.
   */
  onPushedChange?: (pushed: boolean) => void;
}
```

**Type: AgreementV4IndentPushableTriggerProps**

```typescript
export interface AgreementV4IndentPushableTriggerProps {
  /**
   * 클릭하면 하위 콘텐츠가 들여쓰기 되는 영역에 포함될 자식 요소들을 나타내요.
   * 이 컴포넌트는 클릭했을 때 하위 콘텐츠의 들여쓰기를 제어하는 역할을 해요.
   */
  children: React.ReactNode;
}
```

**Type: AgreementV4IndentPushableContentProps**

```typescript
export interface AgreementV4IndentPushableContentProps {
  /**
   * 들여쓰기 가능한 콘텐츠 내에 포함될 자식 요소들을 나타내요.
   * 이 컴포넌트는 트리거가 활성화되면 들여쓰기가 적용되는 콘텐츠를 포함해요.
   */
  children?: React.ReactNode;
}
```

**Type: AgreementV4CollapsibleProps**

```typescript
export interface AgreementV4CollapsibleProps {
  /**
   * 약관을 접거나 펼치기가 가능한 컴포넌트 내에 포함될 자식 요소들을 나타내요.
   */
  children: React.ReactNode;
  /**
   * `Collapsible` 컴포넌트가 현재 접혀 있는지 여부를 나타내요.
   * `true`일 때는 접혀있고, `false`일 때는 펼쳐져 있어요.
   * 이 속성을 사용하면 외부 컴포넌트에서 접기/펼치기 상태를 제어할 수 있어요.
   */
  collapsed?: boolean;
  /**
   * `Collapsible` 컴포넌트의 초기 접기 상태를 설정해요.
   * `true`일 때는 초기 상태가 접혀 있고, `false`일 때는 펼쳐져 있어요.
   */
  defaultCollapsed?: boolean;
  /**
   * 약관을 접거나 펼칠 때 상태가 변경될 때 호출되는 콜백 함수에요.
   * 상태가 변경되면 `collapsed` 값이 인자로 전달돼요.
   * 이 함수를 사용하면 상태 변화를 감지하고 처리할 수 있어요.
   */
  onCollapsedChange?: (collapsed: boolean) => void;
}
```

**Type: AgreementV4CollapsibleTriggerProps**

```typescript
export interface AgreementV4CollapsibleTriggerProps {
  /**
   * 약관을 접거나 펼칠 때 함께 보일 자식 요소들을 나타내요.
   * `CollapsibleTrigger` 컴포넌트는 사용자가 클릭하여 콘텐츠를 접거나 펼칠 수 있는 트리거 역할을 해요.
   */
  children: React.ReactNode;
}
```

**Type: AgreementV4CollapsibleContentProps**

```typescript
export interface AgreementV4CollapsibleContentProps {
  /**
   * 약관을 접거나 펼치기가 가능한 콘텐츠 내에 포함될 자식 요소들을 나타내요.
   * `CollapsibleContent` 컴포넌트는 트리거가 활성화되면 표시되는 콘텐츠를 포함해요.
   */
  children: React.ReactNode;
}
```

**Type: AgreementV4GroupProps**

```typescript
export interface AgreementV4GroupProps {
  /**
   * `Group` 컴포넌트 내부의 요소들 왼쪽에 세로로 표시되는 그라데이션 라인의 표시 여부를 설정해요.
   * `true`일 때는 그라데이션이 표시되고, `false`일 때는 표시되지 않아요.
   * @default true
   */
  showGradient?: boolean;
  /**
   * 그룹 내에 포함될 자식 요소들을 나타내요.
   */
  children: React.ReactNode;
}
```

---

# 래핑한 컴포넌트 활용하기 (/tds-mobile/components/Asset/asset/)

# 래핑한 컴포넌트 활용하기

많이 사용되는 `Frame` 컴포넌트와 `ContentIcon` 컴포넌트, `ContentImage` 컴포넌트, `ContentLottie` 컴포넌트, `ContentText` 컴포넌트, `ContentVideo` 컴포넌트의 조합을 미리 래핑하여 사용하기 쉽게 제공해요.

[Preview: BasicForAsset]

래핑된 컴포넌트들은 다음과 같아요:

- `Asset.Icon` = `Frame` + `ContentIcon`
- `Asset.Image` = `Frame` + `ContentImage`
- `Asset.Lottie` = `Frame` + `ContentLottie`
- `Asset.Text` = `Frame` + `ContentText`
- `Asset.Video` = `Frame` + `ContentVideo`

래핑된 컴포넌트들은 원래 `Frame` 컴포넌트의 `shape` 속성을 `frameShape` 속성으로 이름을 변경해서 제공해요. 예를 들면 다음 예시와 같아요.

```tsx
// Frame을 직접 사용할 때
<Frame shape={{ width: 100, height: 100 }} {...restProps} />

// 래핑된 컴포넌트를 사용할 때
<Asset.Image frameShape={{ width: 100, height: 100 }} {...restProps} />
```

자주 사용되는 frameShape 값들은 미리 정의된 프리셋으로도 제공돼요:

```tsx
<Asset.Image frameShape={Asset.frameShape.SquareMedium} {...restProps} />
```

이 컴포넌트들을 사용하면 쉽게 `Asset` 컴포넌트를 활용할 수 있어요.

## 사용 예제

### 아이콘 에셋 사용하기

`Asset.Icon` 컴포넌트는 아이콘을 표시할 때 사용해요. 아이콘을 프레임 안에 일관된 크기와 스타일로 표현할 수 있어요. 필요에 따라 크기와 색상을 조절할 수 있어요.

**Example: IconAsset**

```tsx

```

#### 색상 변경하기

`color` 속성을 사용해 아이콘의 색상을 변경할 수 있어요. CSS 색상값을 지원해요. 토스의 색상 시스템인 adaptive 값도 사용할 수 있어요.

**Example: ColorIconAsset**

```tsx
<div style={{ display: "flex", flexDirection: "row", gap: "32px" }}></div>
```

### 이미지 에셋 사용하기

`Asset.Image` 컴포넌트는 이미지를 표시할 때 사용해요. `frameShape` 속성을 통해 크기와 모양을 지정할 수 있고, `scaleType` 속성으로 이미지 맞춤 방식을 조절할 수 있어요.

**Example: ImageAsset**

```tsx

```

### 로티 에셋 사용하기

`Asset.Lottie` 컴포넌트는 Lottie 애니메이션을 표시할 때 사용해요.

**Example: LottieAsset**

```tsx

```

### 텍스트 에셋 사용하기

`Asset.Text` 컴포넌트는 텍스트를 프레임 안에 표시할 때 사용해요.

**Example: TextAsset**

```tsx
<Asset.Text
  frameShape={{
    height: 100,
    width: 100,
  }}
>
  Text
</Asset.Text>
```

### 비디오 에셋 사용하기

`Asset.Video` 컴포넌트는 비디오를 재생할 때 사용해요. 자동재생, 반복재생, 음소거를 통해 제어할 수 있어요.

**Example: VideoAsset**

```tsx

```

#### 비디오 제어하기

`Asset.Video` 컴포넌트는 다양한 속성을 통해 비디오 재생을 제어할 수 있어요:

- `controls`: 재생, 일시정지, 음량, 전체화면 등의 컨트롤러를 표시할 수 있어요
- `autoPlay`: 비디오가 로드되면 자동으로 재생할지 설정할 수 있어요
- `loop`: 비디오가 끝나면 다시 처음부터 재생할지 설정할 수 있어요
- `muted`: 비디오의 음소거 여부를 설정할 수 있어요

**Example: ControlVideoAsset**

```tsx

```

## 인터페이스

**Type: IconProps**

```typescript
export interface IconProps extends AssetCommonType {
  /**
   * 아이콘의 이름을 지정해요.
   */
  name: string;

  /**
   * 아이콘의 색상을 지정해요.
   */
  color?: string;
}
```

**Type: ImageProps**

```typescript
export interface ImageProps extends AssetCommonType {
  /**
   * 이미지의 URL을 지정해요.
   */
  src: string;

  /**
   * 이미지가 프레임에 맞춰지는 방식을 지정해요.
   * - `fit`: 이미지의 비율을 유지하면서 프레임 안에 모두 들어가도록 맞춰요
   * - `crop`: 이미지가 프레임을 가득 채우도록 맞추고, 넘치는 부분은 잘라내요
   *
   * @default 'fit'
   */
  scaleType?: "fit" | "crop";

  /**
   * 이미지의 대체 텍스트를 지정해요.
   */
  alt?: string;
}
```

**Type: VideoProps**

```typescript
export interface VideoProps extends AssetCommonType {
  /**
   * 비디오의 URL을 지정해요.
   */
  src: string;

  /**
   * 자동 재생 여부를 지정해요.
   *
   * @default true
   */
  autoPlay?: boolean;

  /**
   * 반복 재생 여부를 지정해요.
   *
   * @default true
   */
  loop?: boolean;

  /**
   * 음소거 여부를 지정해요.
   *
   * @default true
   */
  muted?: boolean;

  /**
   * 컨트롤 표시 여부를 지정해요.
   *
   * @default false
   */
  controls?: boolean;

  /**
   * 비디오를 인라인으로 재생할지 지정해요.
   *
   * @default true
   */
  playsInline?: boolean;
}
```

**Type: LottieProps**

```typescript
export interface LottieProps extends AssetCommonType {
  /**
   * Lottie 애니메이션 파일의 URL을 지정해요.
   *
   * @required
   */
  src: string;

  /**
   * 애니메이션이 프레임에 맞춰지는 방식을 지정해요.
   *
   * @default 'fit'
   */
  scaleType?: "fit" | "crop";
}
```

**Type: TextProps**

```typescript
export interface TextProps extends AssetCommonType {
  /**
   * 텍스트 내용을 지정해요.
   */
  children?: React.ReactNode;
}
```

**Type: AssetCommonType**

```typescript
export interface AssetCommonType {
  /**
   * 프레임의 형태와 크기를 지정해요.
   */
  frameShape?: "FrameShapeType";

  /**
   * 프레임의 배경색을 지정해요.
   */
  backgroundColor?: string;

  /**
   * `Asset` 컴포넌트의 ID를 지정해요.
   */
  id?: string;

  /**
   * `Asset` 컴포넌트의 클래스명을 지정해요.
   */
  className?: string;

  /**
   * 컴포넌트의 인라인 스타일을 지정해요.
   */
  style?: React.CSSProperties;

  /**
   * 프레임에 추가할 액세서리 요소를 지정해요.
   */
  acc?: React.ReactNode;

  /**
   * 액세서리의 위치를 지정해요.
   *
   * @default 'bottom-right'
   */
  accPosition?: "FrameAccPositionType";

  /**
   * 여러 개의 항목이 합쳐졌음을 보여주고 싶을 때 사용해요.
   *
   * `color` 속성으로 오버랩 색상을 설정할 수 있어요.
   */
  overlap?: { color: string } | null;
}
```

---

# Asset 이해하기 (/tds-mobile/components/Asset/check-first/)

# Asset 이해하기

[Image: Asset thumbnail - asset/asset/Thumbnail-Asset.png]

이 문서를 읽고나면,

- `Asset` 컴포넌트의 기본 개념과 구조를 이해할 수 있어요
- `Frame` 컴포넌트의 역할과 중요성을 이해할 수 있어요
- 각 에셋 종류의 특징과 차이점을 이해할 수 있어요

[Preview: BasicForCheckFirst]

## Asset의 구조 이해하기

`Asset` 컴포넌트는 아이콘, 이미지, 비디오, Lottie 애니메이션 등 다양한 미디어 에셋을 일관된 방식으로 표시할 수 있게 해주는 컴포넌트예요.

`Asset` 컴포넌트는 Frame, Content, Union으로 나뉘어요.

> `Asset` 컴포넌트의 핵심은 `Frame` 컴포넌트에요. `Frame` 컴포넌트는 모든 `Asset` 컴포넌트 종류에 일관된 레이아웃과
> 스타일링을 제공하는 기반이 돼요.

### Frame

- `Asset` 컴포넌트의 기본 틀을 담당해요
- 모든 종류의 `Asset` 컴포넌트에 일관된 크기와 모양을 제공해요
- 정사각형, 직사각형, 원형 등 다양한 프리셋을 제공해요

### Content

- 이미지, 아이콘, 비디오, 텍스트, 로띠와 같은 `Asset` 컴포넌트의 실제 내용물이 들어가는 영역이에요
- `scaleType` 속성을 통해 내용물이 프레임에 맞춰지는 방식을 조절할 수 있어요

### Union

- Content에 대한 부가적인 정보를 표현해요
- `overlap`: 여러 항목이 겹쳐있음을 표현해요
- `acc` (액세서리): 상태나 부가 기능을 작은 요소로 표시해요

---

# Asset 활용하기 (/tds-mobile/components/Asset/frame/)

# Asset 활용하기

모든 `Asset` 컴포넌트는 `Frame` 컴포넌트를 기반으로 만들어져 있어요. `Frame` 컴포넌트는 에셋의 크기, 모양, 배경 등 일관된 스타일을 제공하는 역할을 해요.

[Preview: PresetFrameAsset]

## 사용 예제

### Frame 컴포넌트 사용해보기

`Asset` 컴포넌트는 `Frame` 컴포넌트를 기반으로 구성되어 있어요. `Frame` 컴포넌트는 모든 종류의 `Asset` 컴포넌트의 기본 틀이 되어 일관된 레이아웃과 스타일링을 제공하고 있어요.
예를 들어 `Asset.Image` 컴포넌트는 내부적으로 `Frame` 컴포넌트와 `ContentImage` 컴포넌트의 조합으로 이루어져 있어요:

- `Frame` 컴포넌트: 크기, 모양, 배경색, 액세서리 등 에셋의 외형을 담당해요.
- `ContentImage` 컴포넌트: 실제 이미지를 표시하는 역할이에요.

가장 기본적인 사용법을 먼저 살펴보아요.

**Example: FrameContentImageAsset**

```tsx
}
/>
```

위 예시에서 `src`는 `ContentImage` 컴포넌트에 전달되어 실제 이미지를 표시하게 돼요.
여기에 `Frame` 컴포넌트의 특성을 활용하면 다양한 스타일링이 가능해요.
`Frame` 컴포넌트와 `ContentImage` 컴포넌트를 조합하여 쉽게 사용할 수 있게 `Asset.Image` 컴포넌트로 제공해요.

> `Asset.Image` 컴포넌트를 활용한 방법은 **[래핑한 컴포넌트 활용하기](/components/Asset/asset)** 페이지에서 확인할 수
> 있어요.

앞으로 `Asset.Image` 컴포넌트와 `Asset.Lottie` 컴포넌트를 기준으로 설명해요.

### 프리셋 프레임 활용하기

자주 사용되는 크기와 모양의 프레임을 프리셋으로 제공해요.

- **Square**: 정사각형 프레임 (Small, Medium, Large)
- **Rectangle**: 직사각형 프레임 (Medium, Large)
- **Circle**: 원형 프레임 (Small, Medium, Large)
- **Card**: 카드형 프레임 (Small, Medium, Large)

> **Asset.frameShape**에서 원하는 프리셋을 선택할 수 있어요.

**Example: PresetFrameAsset**

```tsx
<div style={{ display: "flex", flexDirection: "column", gap: "32px" }}>
  {/* Square 프리셋 */}
  <div style={{ display: "flex", alignItems: "center", gap: "16px" }}>
    <span style={{ width: 80 }}>Square</span>
  </div>

  {/* Rectangle 프리셋 */}
  <div style={{ display: "flex", alignItems: "center", gap: "16px" }}>
    <span style={{ width: 80 }}>Rectangle</span>
  </div>

  {/* Circle 프리셋 */}
  <div style={{ display: "flex", alignItems: "center", gap: "16px" }}>
    <span style={{ width: 80 }}>Circle</span>
  </div>

  {/* Card 프리셋 */}
  <div style={{ display: "flex", alignItems: "center", gap: "16px" }}>
    <span style={{ width: 80 }}>Card</span>
  </div>
</div>
```

### 액세서리 추가하기

에셋에 부수적인 기능을 표현하기 위해 작은 요소(뱃지 등)를 추가할 수 있어요. 주로 에셋의 모서리에 올라가는 형태로, 뱃지나 상태 표시 등의 용도로 사용돼요.
우리는 이렇게 추가한 요소를 액세서리라고 부르고 있어요.

- `acc` 속성으로 액세서리 컴포넌트를 지정할 수 있어요.
- `accPosition` 속성으로 액세서리의 위치를 지정할 수 있어요. `top-left`, `bottom-left`, `top-right`, `bottom-right`을 사용할 수 있고, 기본적으로는 `bottom-right` 이에요.

**Example: AccPresetFrameAsset**

```tsx
<div style={{ display: 'flex', alignItems: 'center', gap: '16px' }}>
  }
    accPosition="bottom-right"
  />
  }
    accPosition="bottom-right"
  />
  }
    accPosition="bottom-right"
  />
</div>
```

### 오버랩 추가하기

프레임에 오버랩 효과를 추가할 수 있어요. 여러 개의 항목이 합쳐졌음을 보여주고 싶을 때 사용해요. `overlap` 속성으로 테두리 색상을 지정할 수 있어요.
뒤의 배경에는 컬러값을 받을 수 있어요.

**Example: OverlapPresetFrameAsset**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: "16px" }}></div>
```

### 프레임 맞춤 방식 조절하기

`scaleType` 속성으로 이미지가 프레임에 맞춰지는 방식을 조절할 수 있어요:

- `fit`: 이미지의 비율을 유지하면서 프레임 안에 모두 들어가도록 맞춰요.
- `crop`: 이미지가 프레임을 가득 채우도록 맞추고, 넘치는 부분은 잘라내요.

**Example: ScaleTypeLottieAsset**

```tsx
<div style={{ display: "flex", flexDirection: "row", gap: "32px" }}></div>
```

### 프레임 크기 조절하기

`frameShape`의 width와 height로 텍스트가 들어갈 프레임의 크기를 지정할 수 있어요.

**Example: FrameTextAsset**

```tsx
<div style={{ display: "flex", flexDirection: "row", gap: "32px" }}>
  <Asset.Text
    frameShape={{
      height: 200,
      width: 200,
    }}
    backgroundColor={colors.greyBackground}
  >
    Text
  </Asset.Text>

  <Asset.Text
    frameShape={{
      height: 100,
      width: 200,
    }}
    backgroundColor={colors.greyBackground}
  >
    Text
  </Asset.Text>
</div>
```

## 인터페이스

**Type: FrameShapeType**

```typescript
export interface FrameShapeType {
  /**
   * 프레임의 너비를 지정해요.
   */
  width?: string | number;

  /**
   * 프레임의 높이를 지정해요.
   */
  height?: string | number;

  /**
   * 프레임의 모서리 둥글기를 지정해요.
   */
  radius?: string | number;

  /**
   * 프레임의 액세서리 영역 설정이에요.
   */
  acc?: "FrameAccShapeType";

  /**
   * 프레임 뒤에 겹침 효과를 설정해요.
   *
   * 여러 개의 항목이 합쳐졌음을 표현할 때 사용해요.
   */
  overlap?: "FrameOverlapShapeType";
}
```

**Type: FrameAccShapeType**

```typescript
export interface FrameAccShapeType {
  /**
   * 액세서리의 너비를 지정해요.
   */
  width?: string | number;

  /**
   * 액세서리의 높이를 지정해요.
   */
  height?: string | number;

  /**
   * 액세서리의 X축 위치를 지정해요.
   */
  x?: string | number;

  /**
   * 액세서리의 Y축 위치를 지정해요.
   */
  y?: string | number;
}
```

**Type: FrameOverlapShapeType**

```typescript
export interface FrameOverlapShapeType {
  /**
   * 오버랩의 X축 오프셋을 지정해요.
   */
  x?: string | number;

  /**
   * 오버랩의 Y축 오프셋을 지정해요.
   */
  y?: string | number;

  /**
   * 오버랩의 블러 정도를 지정해요.
   */
  blur?: string | number;

  /**
   * 오버랩의 확산 정도를 지정해요.
   */
  spread?: string | number;
}
```

**Type: FrameProps**

```typescript
export interface FrameProps extends Omit<
  React.ComponentPropsWithoutRef<"div">,
  "content"
> {
  /**
   * `Frame` 컴포넌트 내부에 표시될 요소예요.
   *
   * `Asset` 컴포넌트의 주요 콘텐츠(아이콘, 이미지, 비디오 등)가 `content`를 통해 전달돼요.
   */
  content: React.ReactNode;

  /**
   * `Frame` 컴포넌트의 크기와 모양을 정의하는 객체예요.
   *
   * 리소스 타입 별 권장하는 규격을 프리셋으로 제공하고 있어요.
   *
   * @example
   * Asset.frameShape.SquareMedium
   */
  shape: "FrameShapeType";

  /**
   * `Frame` 컴포넌트의 배경색을 지정해요.
   *
   * @default adaptive.grey100
   */
  backgroundColor?: string;

  /**
   * `Frame` 컴포넌트 위에 표시될 추가 요소예요.
   *
   * 뱃지나 상태 표시, 이미지 등을 통해 에셋에 부수적인 기능이 있음을 표현할 때 사용해요.
   */
  acc?: React.ReactNode;

  /**
   * 액세서리(`acc`)의 위치를 지정해요.
   *
   * `top-left`, `top-right`, `bottom-left`, `bottom-right` 중 하나를 선택할 수 있어요.
   *
   * @default 'bottom-right'
   */
  accPosition?: "top-left" | "top-right" | "bottom-left" | "bottom-right";

  /**
   * 액세서리(`acc`) 아래 콘텐츠의 마스킹 처리 방식을 지정해요.
   *
   * `circle`로 설정하면 액세서리 아래 원형으로 콘텐츠가 마스킹돼요.
   *
   * @default 'none'
   */
  accMasking?: "circle" | "none";

  /**
   * `Frame` 컴포넌트에 오버랩을 추가해요.
   *
   * 여러 개의 항목이 합쳐졌음을 보여주고 싶을 때 사용해요.
   */
  overlap?: { color: string } | null;

  /**
   * `Frame` 컴포넌트 내부 콘텐츠의 색상을 지정해요.
   *
   * 주로 아이콘의 색상을 지정할 때 사용돼요.
   */
  color?: string;
}
```

---

# Badge (/tds-mobile/components/badge/)

# Badge

[Image: Badge thumbnail - badge/Thumbnail-Badge.png]

`Badge` 컴포넌트는 항목의 상태를 빠르게 인식할 수 있도록 강조하는 데 사용돼요.

[Preview: Badge]

## 사용법

### 크기 조정하기

`Badge` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. `xsmall`, `small`, `medium`, `large` 중 하나를 선택할 수 있어요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Badge size="xsmall" color="blue" variant="fill">
    xsmall
  </Badge>
  <Badge size="small" color="blue" variant="fill">
    small
  </Badge>
  <Badge size="medium" color="blue" variant="fill">
    medium
  </Badge>
  <Badge size="large" color="blue" variant="fill">
    large
  </Badge>
</div>
```

### 스타일

`Badge` 컴포넌트의 스타일을 설정하려면 `variant` 속성을 사용하세요. 선택 할 수 있는 값에는 `fill`과 `weak`이 있어요.
이때, `color` 속성을 사용하여 원하는 색상을 설정할 수 있어요.

#### fill

`fill` 스타일은 채도가 높아 시각적으로 강렬하고 눈에 띄는 디자인이라 주요 항목을 강조하는 데 적합해요.

**Example: Fill**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Badge size="xsmall" color="blue" variant="fill">
    Badge
  </Badge>
  <Badge size="xsmall" color="teal" variant="fill">
    Badge
  </Badge>
  <Badge size="xsmall" color="green" variant="fill">
    Badge
  </Badge>
  <Badge size="xsmall" color="red" variant="fill">
    Badge
  </Badge>
</div>
```

#### weak

`weak` 스타일은 채도가 낮아서 시각적으로 덜 눈에 띄어요.

**Example: Weak**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Badge size="xsmall" color="blue" variant="weak">
    Badge
  </Badge>
  <Badge size="xsmall" color="teal" variant="weak">
    Badge
  </Badge>
  <Badge size="xsmall" color="green" variant="weak">
    Badge
  </Badge>
  <Badge size="xsmall" color="red" variant="weak">
    Badge
  </Badge>
</div>
```

## 인터페이스

**Type: BadgeProps**

```typescript
export interface BadgeProps {
  /**
   * `Badge` 컴포넌트의 색상과 투명도 정보에요.
   */
  variant: "fill" | "weak";
  /**
   * `Badge` 컴포넌트의 크기에요.
   */
  size: "xsmall" | "small" | "medium" | "large";
  /**
   * `Badge` 컴포넌트의 색상이에요.
   */
  color: "blue" | "teal" | "green" | "red" | "yellow" | "elephant";
}
```

---

# Board Row (/tds-mobile/components/board-row/)

# Board Row

`BoardRow`는 제한된 공간에서 많은 정보를 깔끔하게 정리해 표시하는 컴포넌트예요. 주로 Q&A와 같은 정보를 표현할 때 사용하며, 펼쳐졌다 접히는 방식으로 정보를 보여주는 아코디언 컴포넌트 같은 역할을 해요.

[Preview: BoardRow]

## 사용법

`BoardRow` 컴포넌트는 제목, 프리픽스, 아이콘, 그리고 콘텐츠 영역으로 구성돼요. 사용자는 제목 영역을 클릭하여 콘텐츠 영역을 열거나 닫을 수 있어요. 제목 옆의 프리픽스와 아이콘은 추가적인 정보나 상태를 시각적으로 표시하기 위해 사용해요.

**Example: Basic**

```tsx
<BoardRow
  title="매도 환전이 무엇인가요?"
  prefix={<BoardRow.Prefix>Q</BoardRow.Prefix>}
  icon={}
>
  <BoardRow.Text>
    주식 거래가 실시간이 아니기 때문에 가격이 변할 것에 대비하는 금액을
    말해요.{" "}
  </BoardRow.Text>
</BoardRow>
```

### 패널 초기 열림 상태 제어하기

`initialOpened` 속성을 사용하면 패널이 처음 화면에 렌더링될 때, 기본적으로 열린 상태로 표시돼요. 즉, 사용자가 별도로 클릭하지 않아도 처음부터 콘텐츠 영역이 펼쳐져 있어요.

**Example: Initial**

```tsx
<BoardRow
  initialOpened
  title="매도 환전이 무엇인가요"
  prefix={<BoardRow.Prefix>Q</BoardRow.Prefix>}
  icon={}
>
  <BoardRow.Text>초기부터 콘텐츠 영역이 열려 있어요.</BoardRow.Text>
</BoardRow>
```

### 패널 열림/닫힘 제어하기

`isOpened` 속성과 `onOpen`, `onClose` 함수를 사용하면 컴포넌트 외부에서 패널의 열림/닫힘 상태를 직접 제어할 수 있어요. `isOpened`가 `true`면 패널이 열린 상태로, `false`면 닫힌 상태로 표시돼요. `onOpen`은 패널이 열릴 때 호출되는 함수이고, `onClose`는 패널이 닫힐 때 호출되는 함수예요. 이 속성과 함수들을 활용해서 패널의 상태를 외부에서 동적으로 제어할 수 있어요.

**Example: OpenClose**

```tsx
function OpenClose() {
  const [isOpened, setIsOpened] = React.useState(false);
  return (
    <BoardRow
      title="매도 환전이 무엇인가요"
      isOpened={isOpened}
      onOpen={() => setIsOpened(true)}
      onClose={() => setIsOpened(false)}
      prefix={<BoardRow.Prefix>Q</BoardRow.Prefix>}
      icon={}
    >
      <BoardRow.Text>
        주식 거래가 실시간이 아니기 때문에 가격이 변할 것에 대비하는 금액을
        말해요.
      </BoardRow.Text>
    </BoardRow>
  );
}
```

### 콘텐츠 영역 채우기

`BoardRow`의 콘텐츠 영역에는 주로 `Post` 컴포넌트를 사용해요. `Post` 컴포넌트를 활용하면 깔끔하게 정리된 정보를 전달할 수 있어요.

**Example: FillContent**

```tsx
<BoardRow
  title="질문을 적어주세요."
  prefix={<BoardRow.Prefix>Q</BoardRow.Prefix>}
  icon={}
  initialOpened
>
  <Post.Paragraph paddingBottom={24} typography="t6">
    주식 거래가 실시간이 아니기 때문에 가격이 변할 것에 대비하는 금액을 말해요.
  </Post.Paragraph>
  <Post.Ul paddingBottom={24} typography="t6">
    <Post.Li>
      대시를 붙이고 띄어쓰면 불렛을 쓸 수 있어요.
      <Post.Ul paddingBottom={24} typography="t6">
        <Post.Li>들여쓰려면 대시 앞에 〉를 입력해요.</Post.Li>
      </Post.Ul>
    </Post.Li>
  </Post.Ul>
</BoardRow>
```

간단한 문장을 사용할 때는 `BoardRow.Text`를 사용할 수 있어요. `BoardRow.Text`는 `Post.Paragraph`를 확장한 컴포넌트예요.

**Example: SimpleContent**

```tsx
<BoardRow
  title="질문을 적어주세요."
  prefix={<BoardRow.Prefix>Q</BoardRow.Prefix>}
  icon={}
  initialOpened
>
  <BoardRow.Text>
    주식 거래가 실시간이 아니기 때문에 가격이 변할 것에 대비하는 금액을 말해요.
  </BoardRow.Text>
</BoardRow>
```

## 접근성

`BoardRow` 컴포넌트는 기본적으로 접근성을 지원하는 여러 속성을 포함하고 있어요. 이 속성들은 스크린 리더 사용자들이 컴포넌트를 명확하게 이해하고 상호작용할 수 있도록 도와줘요. 특히 컴포넌트에서 패널의 열림/닫힘 상태는 시각적으로만 나타나는 것이 아니라, 스크린 리더 사용자에게도 전달될 수 있도록 설계되었어요.

| 속성            | 접근성 효과                                     | 설명                                                         |
| --------------- | ----------------------------------------------- | ------------------------------------------------------------ |
| `<button>` 태그 | 스크린 리더가 버튼으로 인식해요.                | 사용자는 제목 영역이 클릭 가능한 버튼임을 알 수 있어요.      |
| `aria-expanded` | 패널이 열림/닫힘 상태를 스크린 리더가 알려줘요. | 사용자는 패널이 현재 열려 있는지 닫혀 있는지를 알 수 있어요. |

### 사용 방법 예시

```jsx
<BoardRow
  title="매도 환전이 무엇인가요?"
  isOpened={true} // 패널이 열린 상태로 시작, 자동으로 aria-expanded="true" 적용
  prefix={<BoardRow.Prefix>Q</BoardRow.Prefix>}
  icon={<BoardRow.ArrowIcon />}
>
  <BoardRow.Text>
    주식 거래가 실시간이 아니기 때문에 가격이 변할 것에 대비하는 금액을 말해요.
  </BoardRow.Text>
</BoardRow>
```

`BoardRow`는 스크린 리더 사용자들을 위한 `aria-expanded` 속성을 자동으로 추가하거나 제거해서 패널의 상태를 스크린 리더에 전달해요. 그래서 추가적인 접근성 설정을 하지 않아도 기본적인 상호작용을 보장할 수 있어요.

## 인터페이스

**Type: BoardRowProps**

```typescript
export interface BoardRowProps {
  /**
   * 컴포넌트가 처음 렌더링될 때 열려 있을지 여부를 설정해요. `true`로 설정하면 콘텐츠가 처음부터 열려 있어요.
   *
   * @default false
   */
  initialOpened?: boolean;

  /**
   * 이 값이 `true`일 때 콘텐츠 영역이 열린 상태로 표현돼요. `BoardRow` 컴포넌트의 상태를 컴포넌트 외부에서 관리할 때, `onOpen`과 `onClose` 속성과 함께 사용해요.
   *
   * @default false
   */
  isOpened?: boolean;

  /**
   * 콘텐츠 영역이 열릴 때 호출되는 함수예요.
   */
  onOpen?: () => void;

  /**
   * 콘텐츠 영역이 닫힐 때 호출되는 함수예요.
   */
  onClose?: () => void;

  /**
   * 헤더 영역에 표시될 제목이에요.
   */
  title: ReactNode;

  /**
   * 헤더 영역의 `title` 앞에 8px 간격으로 글자나 요소를 배치해요.
   * 주로 `BoardRow.Prefix`를 사용해요.
   */
  prefix?: ReactNode;

  /**
   * 헤더 영역의 `title` 뒤에 표시할 아이콘이에요.
   * 주로 `BoardRow.ArrowIcon`를 사용해요.
   */
  icon?: ReactNode;

  /**
   * 콘텐츠 영역에 표시될 내용이에요.
   * 주로 `BoardRow.Text` 혹은 `Post` 컴포넌트로 감싼 요소를 사용해요.
   */
  children?: ReactNode;

  /**
   * `li` 요소에 적용할 HTML 기본 속성들을 지정해요.
   */
  liAttributes?: LiHTMLAttributes<HTMLLIElement>;
}
```

**Type: BoardRowTextProps**

```typescript
export interface BoardRowTextProps {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * @default "t6"
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
}
```

**Type: BoardRowPrefixProps**

```typescript
export interface BoardRowPrefixProps {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * @default "st8"
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";

  /**
   * 텍스트의 두께를 지정해요.
   * @default "regular"
   */
  fontWeight?: FontWeight;

  /**
   * 텍스트의 색상을 지정해요.
   * @default `adaptive.blue500`
   */
  color?: string;
}
```

**Type: BoardRowIconProps**

```typescript
export interface BoardRowIconProps {
  /**
   * 아이콘의 이름을 지정해요.
   * @default "icon-arrow-right-mono"
   */
  name?: string;

  /**
   * 아이콘의 색상을 지정해요.
   * @default `adaptive.grey400`
   */
  color?: string;

  /**
   * 아이콘의 크기를 지정해요.
   * @default 24
   */
  size?: number;
}
```

---

# Border (/tds-mobile/components/border/)

# Border

[Image: Border thumbnail - border/Thumbnail-Border.png]

`Border` 컴포넌트는 요소 주위에 선을 그려서 요소 간의 구분을 명확히 하고 싶을 때 사용해요. UI 요소 간의 명확한 구분과 계층 구조를 표현할 수 있어요.

`Border` 컴포넌트는 주로 리스트나 섹션을 구분하는 데 사용돼요.

[Preview: div]

## 사용법

### 항목 나누기

리스트나 섹션을 나눌 때 `Border` 컴포넌트를 사용할 수 있어요. `variant` 속성에 따라 적용되는 스타일이 다르니, 필요에 따라 적절한 값을 선택하세요.

- `full`: 전체 너비에 맞춰서 선이 그려져요.
- `padding24`: 양쪽에 `24px`의 여백을 두고 선이 그려져요.

**Example: Full**

```tsx
<div
  style={{
    display: 'flex',
    flexDirection: 'column',
    width: 350,
    borderRadius: 20,
    backgroundColor: adaptive.grey100,
  }}
>
  } />

  } />
</div>
```

### 왼쪽에 여백주기

왼쪽 여백이 필요한 경우에는 `variant` 값을 `padding24`로 사용하세요.

**Example: Padding24**

```tsx
<div style={{ display: 'flex', flexDirection: 'column' }}>
  } />

  } />
</div>
```

### 구간 나누기

`Border` 컴포넌트로 구간을 나눈다면, `variant`의 값으로 `height16`을 사용하세요.

**Example: Height16**

```tsx
<div style={{ display: 'flex', flexDirection: 'column' }}>
  } />

  } />
</div>
```

## 인터페이스

**Type: BorderProps**

```typescript
export interface BorderProps {
  /**
   * `Border` 컴포넌트의 형태를 결정해요.
   * `Border` 컴포넌트로 항목을 나눈다면 `full` 또는 `padding24`를 사용하세요.
   * 구간을 나눈다면 `height16`을 사용하세요.
   *
   * @default "full"
   */
  variant?: "full" | "padding24" | "height16";

  /**
   * `variant` 속성의 타입이 `height16` 일 때 `height` 속성을 사용해서 `Border` 컴포넌트의 높이를 커스텀할 수 있어요.
   */
  height?: string;
}
```

---

# Bottom Info (/tds-mobile/components/bottom-info/)

# Bottom Info

`BottomInfo` 컴포넌트는 화면 하단에 중요한 정보나 주의사항을 명확하게 표시할 때 사용해요. 특히 금융 상품처럼 법적 고지나 디스클레이머(면책 조항)를 사용자에게 안내해야 하는 상황에서 유용해요. 주로 리스트 형식을 제공할 수 있는 `Post` 컴포넌트와 함께 사용해 정보를 깔끔하게 정리해 보여줄 수 있어요.

[Preview: div]

## 사용 예제

### 그라디언트

`BottomInfo` 컴포넌트의 하단 그라디언트를 변경하려면 `bottomGradient` 속성을 사용하세요. `bottomGradient` 속성을 추가하면 화면 최하단 스크롤시 배경색과 바텀인포의 색이 달라 일관성이 떨어지는 문제를 해결할 수 있어요.

#### 그라디언트 조정하기

`bottomGradient` 기본값은 `linear-gradient(adaptive.greyBackground, rgba(255,255,255,0))`이고, 원하는 값으로 변경할 수 있어요.

**Example: BottomGradient**

```tsx
<div style={{ width: "100%", maxWidth: 375, margin: "auto" }}>
  <BottomInfo
    bottomGradient={`linear-gradient(${adaptive.greyBackground}, ${adaptive.blue100})`}
  >
    <Post.Ul paddingBottom={24} typography="t7">
      <Post.Li>
        대출기간 40년의 경우 만39세 (만 나이를 사용해주세요!) 이하 또는
        신혼부부(혼인신고후 7년이내) 대상으로 한 상품입니다.
      </Post.Li>
      <Post.Li>
        회사 및 대출모집인은 해당상품에 대해 충분히 설명할 의무가 있으며,
        고객님께서는 이에 대한 충분한 설명을 받으시길 바랍니다.
      </Post.Li>
      <Post.Li>
        대출금 중도상환시 중도상환수수료 부과기간 잔여일수에 대해
        중도상환수수료가 발생할 수 있습니다.
      </Post.Li>
    </Post.Ul>
  </BottomInfo>
</div>
```

#### 그라디언트 없애기

`bottomGradient` 속성을 `none`으로 그라디언트를 없앨 수 있어요. `none`을 사용하면 iOS 기기에서 기본 배경색과 어울리지 않을 수 있어서, 특별한 경우가 아니라면 사용을 권장하지 않아요

**Example: BottomGradientNone**

```tsx
<div style={{ width: "100%", maxWidth: 375, margin: "auto" }}>
  <BottomInfo bottomGradient="none">
    <Post.Ul paddingBottom={24} typography="t7">
      <Post.Li>
        대출기간 40년의 경우 만39세 (만 나이를 사용해주세요!) 이하 또는
        신혼부부(혼인신고후 7년이내) 대상으로 한 상품입니다.
      </Post.Li>
      <Post.Li>
        회사 및 대출모집인은 해당상품에 대해 충분히 설명할 의무가 있으며,
        고객님께서는 이에 대한 충분한 설명을 받으시길 바랍니다.
      </Post.Li>
      <Post.Li>
        대출금 중도상환시 중도상환수수료 부과기간 잔여일수에 대해
        중도상환수수료가 발생할 수 있습니다.
      </Post.Li>
    </Post.Ul>
  </BottomInfo>
</div>
```

## 인터페이스

**Type: BottomInfoProps**

```typescript
export interface BottomInfoProps {
  /**
   * 하단 그라데이션의 배경색과 존재 유무를 설정해요.
   *
   * @default "linear-gradient(adaptive.greyBackground, rgba(255,255,255,0))"
   */
  bottomGradient?: "none" | "linear-gradient(${string})";
}
```

---

# BottomSheet (/tds-mobile/components/bottom-sheet/)

export function getPreviewBox(PreviewComponent) {
return (
[Preview: VirtualRoot]
);
}

# BottomSheet

`BottomSheet` 컴포넌트는 화면의 하단에서 슬라이드 되어 나타나는 패널이에요.
페이지를 벗어나지 않고 사용자에게 추가적인 상세 설명을 보여주거나, 특정 액션을 유도하고 싶을 때 유용해요.

{getPreviewBox(Basic)}

## 사용 예제

### 제목 붙이기

`BottomSheet`에 제목을 붙이려면 `header` 속성을 사용하세요. 일반적으로 `BottomSheet.Header` 컴포넌트를 넣어 사용해요.

### 부제목 붙이기

`BottomSheet`에 제목을 붙이려면 `headerDescription` 속성을 사용하세요. 일반적으로 `BottomSheet.HeaderDescription` 컴포넌트를 넣어 사용해요.

### CTA 붙이기

`BottomSheet`에 CTA를 붙이려면 `cta` 속성을 사용하세요. 일반적으로 `BottomSheet.CTA` 컴포넌트를 넣어 사용해요.

### Double CTA 붙이기

`BottomSheet.DoubleCTA` 컴포넌트를 사용하면 버튼이 좌우로 나누어진 형태의 CTA도 사용할 수 있어요.

### 선택지 보여주기

`BottomSheet.Select` 컴포넌트를 사용하면 사용자에게 선택지를 보여줄 수 있어요.

## 페이지 포커스 유지하기

`BottomSheet`이 열린 상태에서도 페이지에 포커스를 유지해야 하는 경우에는 `UNSAFE_disableFocusLock` 속성을 사용하세요.
`disableDimmer` 속성을 함께 사용해서 딤 해제도 할 수 있어요.

## 인터페이스

**Type: BottomSheetProps**

```typescript
export interface BottomSheetProps {
  /**
   * `BottomSheet`이 열렸는지 여부예요.
   */
  open: boolean;
  /**
   * `BottomSheet` 영역의 className을 설정해요.
   */
  className?: string;
  /**
   * 딤 영역에 전달할 className이에요.
   */
  dimmerClassName?: string;
  /**
   * 이 값이 `true`일 때 딤 영역을 표시하지 않아요.
   * @default false
   */
  disableDimmer?: boolean;
  /**
   * 이 값이 `true`일 때 `BottomSheet`을 키보드 위로 올려줘요. `BottomSheet` 내부에 키보드를 활성화할 수 있는 컴포넌트가 있을 때 사용되어요.
   * @default false
   */
  hasTextField?: boolean;
  /**
   * `BottomSheet` 제목 영역이에요.
   */
  header?: React.ReactNode | React.ReactElement[];
  /**
   * `BottomSheet` 부제목 영역이에요.
   */
  headerDescription?: React.ReactNode | React.ReactElement[];
  /**
   * `BottomSheet` CTA 영역이에요.
   */
  cta?: React.ReactNode;
  /**
   * `BottomSheet`의 메인 컨텐츠 영역이에요.
   */
  children?: ReactNode;
  /**
   * HTML의 `aria-labelledby` 속성에 전달할 값이에요.
   * 스크린 리더가 `BottomSheet`의 제목을 읽을 때 사용할 요소의 `ID`를 지정해요.
   * `ID`를 전달하여 `BottomSheet`의 목적을 설명해요.
   *
   * @link {참고} https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby
   */
  ariaLabelledBy?: string;
  /**
   * HTML의 `aria-labelledby` 속성에 전달할 값이에요.
   * 스크린 리더가 BottomSheet의 상세 내용을 읽을 때 사용할 요소의 `ID`를 지정해요.
   * `ID`를 전달하여 BottomSheet의 자세한 설명을 제공해요.
   *
   * @link {참고} https://developer.mozilla.org/ko/docs/Web/Accessibility/ARIA/Attributes/aria-describedby
   */
  ariaDescribedBy?: string;
  /**
   * BottomSheet 내부 컨텐츠의 드래그 동작을 제어해요.
   * 이 값이 `true`라면 컨텐츠 영역에서 드래그해도 BottomSheet이 움직이지 않아요.
   *
   * @default false
   */
  disableChildrenDragging?: boolean;
  /**
   * `BottomSheet` 내부에 스크롤이 있을 때, `BottomSheet`을 위로 10px 드래그하면 화면 전체 높이로 확장되도록 설정해요.
   * @default false
   */
  expandBottomSheet?: boolean;
  /**
   * `BottomSheet`이 확장되지 않았을 때의 `BottomSheet` 높이를 설정해요. 단위는 `px`예요.
   */
  maxHeight?: number;
  /**
   * `BottomSheet`이 확장되었을 때의 높이를 지정해요. 단위는 `px`예요.
   */
  expandedMaxHeight?: number;
  /**
   * `expandBottomSheet`와 `expandBottomSheetWhenScroll`이 모두 `true`일 때, `BottomSheet` 내부에서 스크롤을 내리면 `BottomSheet`이 화면 전체 높이로 확장돼요.
   * @default false
   */
  expandBottomSheetWhenScroll?: boolean;
  /**
   * `BottomSheet`이 닫힐 때 실행할 함수예요.
   */
  onClose?: () => void;
  /**
   * `BottomSheet`이 확장되었을 때 호출되는 함수예요.
   */
  onExpanded?: () => void;
  /**
   * `BottomSheet`의 상단의 핸들러에 터치가 시작되었을 때 실행되는 함수예요.
   */
  onHandlerTouchStart?: (event: React.TouchEvent) => void;
  /**
   * `BottomSheet`의 상단의 핸들러에 터치가 끝났을 때 실행되는 함수예요.
   */
  onHandlerTouchEnd?: (event: React.TouchEvent) => void;
  /**
   * 딤 영역을 클릭 했을 때 실행되는 함수예요.
   */
  onDimmerClick?: () => void;
  /**
   * `BottomSheet`이 열리기 시작할 때 실행되는 함수예요.
   */
  onEntered?: () => void;
  /**
   * `BottomSheet`이 닫히고 완전히 사라진 후 실행되는 함수예요.
   */
  onExited?: () => void;
  /**
   * `BottomSheet`을 렌더링할 HTML 요소를 지정해요. `UNSAFE_disabledFocusLock`이 `true`일 때는 무시돼요.
   * @default document.body
   */
  portalContainer?: HTMLElement | null;
  /**
   * `BottomSheet`컴포넌트 내부의 `BottomSheet.CTA` 컴포넌트와 `children`의 간격을 조정해요. `BottomSheet.Gradient`의 높이와 동일해요.
   *
   * @default 34px
   */
  ctaContentGap?: number;
  /**
   * `BottomSheet`이 열려도 기존 페이지에 포커스 잠금과 스크린 리더 잠금이 적용되지 않도록 설정해요.
   * 이 속성을 사용하면 접근성 대응이 되지 않으므로 직접 접근성을 대응해야 해요.
   */
  UNSAFE_disableFocusLock?: boolean;
  /**
   * 바텀시트 외부의 어두운 배경을 클릭해도 `onClose`가 호출되지 않게 해요.
   *
   * **주의: 바텀시트 외부 영역 클릭 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   */
  UNSAFE_ignoreDimmerClick?: boolean;
  /**
   * 앱에서 제공하는 뒤로가기 이벤트를 무시할지 설정해요.
   * `true`로 설정하면 뒤로가기 동작이 발생해도 바텀시트가 닫히지 않아요.
   *
   * **주의: 뒤로가기 동작 발생 시 사용자의 액션을 취소하고 바텀시트가 닫히는 것이 권장되는 동작이에요.**
   * 이 API는 곧 지원이 중단될 수 있어요. 따라서 취소 동작을 구현하는 것이 기술적으로 어려운 상황에서만 이 속성을 사용하세요.
   */
  UNSAFE_ignoreBackEvent?: boolean;

  /**
   * 더큰텍스트 160% 이상일 때, 헤더를 스크롤 영역에 포함합니다.
   *
   * @default true
   */
  a11yIncludeHeaderInScroll?: boolean;
}
```

**Type: BottomSheetHeaderProps**

```typescript
export interface BottomSheetHeaderProps {
  /**
   * 제목 영역에 전달할 `className`이에요.
   */
  className?: string;
  /**
   * 제목 영역에 전달할 자식 요소에요. 문자열을 넣으면 `h1` 태그로 감싸고, `t4` 텍스트 스타일을 적용해요.
   */
  children: React.ReactNode;
}
```

**Type: BottomSheetHeaderDescriptionProps**

```typescript
export interface BottomSheetHeaderDescriptionProps {
  /**
   * 부제목 영역에 전달할 `className`이에요.
   */
  className?: string;
  /**
   * 부제목 영역에 전달할 자식 요소에요. 부제목은 기본적으로 `t6` 텍스트로 감싸져요.
   */
  children: React.ReactNode;
}
```

**Type: BottomSheetSelectProps**

```typescript
export interface BottomSheetSelectProps {
  /**
   * 각 선택 옵션에 대한 정보예요.
   */
  options: SelectOption[];
  /**
   * 현재 선택된 값이에요.
   */
  value?: string;
  /**
   * 셀렉트 박스에 전달할 `className`이에요.
   */
  className?: string;
  /**
   * `BottomSheet`이 열릴 때 슬라이드 업 애니메이션을 적용할 지 여부예요.
   * @default true
   */
  animation?: boolean;
  /**
   * 애니메이션이 활성화됐을 때, 애니메이션의 지연 시간을 설정해요. 단위는 밀리초(ms)예요.
   */
  animationDelay?: number;
  /**
   * 값이 변경되었을 때 실행할 함수에요. 변경된 값은 `event.target.value`로 확인할 수 있어요.
   */
  onChange: (event: React.ChangeEvent<HTMLInputElement>) => void;
}
```

**Type: SelectOption**

```typescript
export interface SelectOption {
  /**
   * 선택 옵션의 이름이에요. UI에 이 이름이 표시돼요.
   */
  name: string;
  /**
   * 선택 옵션의 값이에요. `onChange` 함수에서 `e.target.value`로 전달되는 값이에요.
   */
  value: string;
  /**
   * 선택 옵션에 전달할 `className`이에요.
   */
  className?: string;
  /**
   * 선택 옵션을 비활성화할지 여부에요.
   */
  disabled?: boolean;
  /**
   * 옵션이 선택되지 않았을 때 체크박스를 숨길 지 여부에요.
   */
  hideUnCheckedCheckBox?: boolean;
}
```

---

# BottomCTA 이해하기 (/tds-mobile/components/BottomCTA/check-first/)

# BottomCTA 이해하기

[Image: BottomCTA thumbnail - bottom-cta/single/Thumbnail-BottomCTA.png]

이 문서를 읽고나면,

- `FixedBottomCTA`와 `BottomCTA`의 차이를 이해할 수 있어요.
- `BottomCTA.Single`와 `BottomCTA.Double`의 차이를 이해할 수 있어요.

## 이해하기

`BottomCTA` 컴포넌트는 사용자 인터페이스(UI)에 표시되는 호출 버튼(Call-to-Action)이에요.  
주로 사용자가 특정 작업을 완료할 수 있도록 도와줄 때 사용하죠. 보통 페이지 하단에 항상 고정되어 있어서, 긴 스크롤이나 키보드 입력 시에도 손쉽게 접근할 수 있어요.

### FixedBottomCTA vs BottomCTA

`FixedBottomCTA`와 `BottomCTA`는 모두 하단에 고정되는 **호출 버튼(Call-to-Action)** 을 제공해요. 차이점은 버튼의 고정 여부에요. `FixedBottomCTA`는 `BottomCTA` 컴포넌트의 `fixed` prop을 `true`로 기본 설정한 컴포넌트에요. 따라서 항상 화면 하단에 고정된 상태로 표시돼요. 다음과 같은 형태로 정의되어 있죠.

```tsx /fixed/
export const FixedBottomCTA = (
  props: Omit<ComponentProps<typeof BottomCTA>, "fixed">,
) => {
  return <BottomCTA fixed={true} {...props} />;
};
```

> `FixedBottomCTA`는 기본적으로 CTA가 하나인 `BottomCTA.Single`에요. 만약 CTA가 두 개인 `Double`를 사용하고 싶다면
> `FixedBottomCTA.Double`를 사용하세요.

> 이 문서에서는 BottomCTA 만을 예시로 설명해요.

### Single vs Double

다음은 `BottomCTA.Single`와 `BottomCTA.Double`의 차이를 비교한 표에요.

| type   | 예시                                                                                                                                        | 설명                                                                                                            | 문서                                        |
| :----- | :------------------------------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------- | :------------------------------------------ |
| Single | <BottomCTA.Single>버튼 하나</BottomCTA.Single>                                                                                              | 버튼이 하나만 렌더링되는 형태에요.<br/>children을 통해 버튼에 렌더링될 요소를 결정해요.                         | [Single 문서](/components/BottomCTA/Single) |
| Double | <BottomCTA.Double leftButton={<CTAButton color="dark" variant="weak">버튼 둘</CTAButton>} rightButton={<CTAButton>버튼 하나</CTAButton>} /> | 버튼이 두 개가 렌더링되는 형태에요.<br/>leftButton, rightButton prop을 통해 각 버튼에 렌더링될 요소를 결정해요. | [Double 문서](/components/BottomCTA/Double) |

---

# Double (/tds-mobile/components/BottomCTA/Double/)

## BottomCTA.Double

`BottomCTA.Double`는 이 BottomCTA의 구성 요소 중 하나로, 버튼을 **두 개** 렌더링하는 형태에요.

[Preview: BottomCTA]

## 사용법

### 배경색 없애기

`BottomCTA.Double` 컴포넌트는 기본적으로 배경색이 있어요. 배경색을 없애려면 `background` prop을 `none`으로 설정하세요.

[Preview: BottomCTA]

### SafeArea의 영향 받지 않기

`hasSafeAreaPadding` prop을 `true`로 설정하면, 기기 화면 하단에 있는 SafeArea의 높이만큼 `paddingBottom`이 추가되어 버튼이 안전하게 표시돼요. 이때 웹뷰에서 user-agent로 전달된 SafeArea 정보를 `--toss-safe-area-bottom` 변수에 반영해 사용해요.

아래 코드와 같이 변수가 선언돼요. 이때 웹뷰로부터 전달받아 파싱된 값이 `--toss-safe-area-bottom` 이에요.
이때 웹뷰로부터 전달받아 파싱된 값이 `--toss-safe-area-bottom` 이에요.

```html
<style>
  --bottom-cta-padding-bottom: max(
    var(--toss-safe-area-bottom, 0px),
    env(safe-area-inset-bottom),
    20px
  );
</style>
```

### 최상단 요소 스타일 변경하기

`containerStyle` prop을 통해 최상단 요소의 스타일을 변경할 수 있어요.

> 모바일 키패드 사용시에는 opacity 혹은 bottom 값을 변경하는 것을 지양해야 해요.

### 상단/하단 요소 추가하기

`topAccessory` 와 `bottomAccessory` prop을 사용하면 상단과 하단에 요소를 추가할 수 있어요.

**Example: Accessory**

```tsx
<BottomCTA.Double
  leftButton={
    <CTAButton color="danger" variant="weak">
      Left
    </CTAButton>
  }
  rightButton={<CTAButton>Right</CTAButton>}
  topAccessory={<div>topAccessory</div>}
  bottomAccessory={<div>bottomAccessory</div>}
/>
```

### 애니메이션 설정하기

`showAfterDelay` prop을 사용하면 지정한 시간만큼 지연된 후에 버튼이 애니메이션과 함께 나타나도록 할 수 있어요.

**Example: ShowAfterDelay**

```tsx
function ShowAfterDelay() {
  const [animation, setAnimation] = React.useState<"fade" | "scale" | "slide">(
    "fade",
  );

  return (
    <>
      <SegmentedControl
        value={animation}
        onChange={setAnimation as (v: string) => void}
      >
        <SegmentedControl.Item value="fade">fade</SegmentedControl.Item>
        <SegmentedControl.Item value="scale">scale</SegmentedControl.Item>
        <SegmentedControl.Item value="slide">slide</SegmentedControl.Item>
      </SegmentedControl>

      <BottomCTA.Double
        showAfterDelay={{ animation, delay: 1 }}
        leftButton={
          <CTAButton color="danger" variant="weak">
            Left
          </CTAButton>
        }
        rightButton={<CTAButton>Right</CTAButton>}
      />
    </>
  );
}
```

### 스크롤에 따라 숨김 처리하기

`hideOnScroll` prop을 `true`로 설정하면, 사용자가 페이지를 스크롤할 때 버튼이 자동으로 숨겨져요.
이때 `hideOnScrollDistanceThreshold` prop을 사용해 버튼이 숨겨지는 스크롤 지점을 설정할 수 있어요.

## 인터페이스

**Type: TypeBProps**

```typescript
export interface TypeBProps {
  /**
   * 초기 등장 애니메이션을 정의해요.
   */
  showAfterDelay?: {
    /**
     * CTA의 초기 등장 애니메이션을 설정하는 속성이에요. 애니메이션 유형은 `slide`, `fade`, `scale` 중 하나를 선택할 수 있어요.
     */
    animation: "slide" | "fade" | "scale";
    /**
     * 초 단위로 등장 애니메이션 지연 시간을 정의해요.
     */
    delay: number;
  };
  /**
   * CTA가 등장하거나 숨겨질 때 애니메이션을 적용할지 여부를 설정해요. 초기 등장 애니메이션과 별도로 동작해요. 기본값은 `false`에요.
   *
   * @default false
   */
  show?: boolean;
  /**
   * 유저가 스크롤 할 때 CTA를 숨길지를 설정해요. `true`로 설정하면 스크롤 위치가 `hideOnScrollDistanceThreshold` 값보다 크면 숨겨지고, 작으면 나타나요.
   *
   * @default false
   */
  hideOnScroll?: boolean;
  /**
   * `hideOnScroll`이 true일 때 넘겨준 값만큼 스크롤이 이동해야 발생해요.
   * 이때 단위는 px이에요.
   *
   * @default 1
   */
  hideOnScrollDistanceThreshold?: number;
  /**
   * 하단 `safeArea`만큼의 `paddingBottom`을 갖게 할지를 결정해요.
   * `hasPaddingBottom`이 `false`라면, `hasSafeAreaPadding` 값에 관계없이 `paddingBottom`이 0px로 고정돼요.
   * `hasPaddingBottom`이 `true`이고 `hasSafeAreaPadding`이 `false`라면 `paddingBottom`은 20px로 설정돼요.
   *
   * @default true
   */
  hasSafeAreaPadding?: boolean;
  /**
   * `false`로 설정하면 CTA의 `paddingBottom` 값이 0이 돼요.
   *
   * @default true
   */
  hasPaddingBottom?: boolean;
  /**
   * `takeSpace`는 컴포넌트가 화면에 고정된 상태에서 레이아웃 공간을 차지할지를 결정해요.
   * `true`라면 `FixedBottomCTA`와 유사하게 고정된 상태에서 공간을 차지하고,
   * `false`라면 화면 하단에 고정되지만 레이아웃에 영향을 미치지 않아요.
   * `fixed`가 `true`일 때는 기본값이 `true`에요.
   */
  takeSpace?: boolean;
  /**
   * 화면 최하단에 고정시킬지 결정해요.
   * BottomCTA에서 `fixed`를 `true`로 설정하면, `FixedBottomCTA`와 똑같이 동작해요.
   */
  fixed?: boolean;
  /**
   * 모바일 키보드가 표시될 때 사용을 권장하지 않는 스타일을 설정하는 객체에요.
   * 모바일 키보드가 있다면 `opacity`와 `bottom` 속성 사용을 피하는 것을 권장해요.
   */
  containerStyle?: React.CSSProperties;
  /**
   * 컨테이너 요소의 `ref`에요.
   */
  containerRef?: Ref<HTMLDivElement>;
  /**
   * 왼쪽 버튼이에요.
   */
  leftButton: ReactNode;
  /**
   * 오른쪽 버튼이에요.
   */
  rightButton: ReactNode;
  /**
   * `none`으로 설정하면 배경색이 제거돼요.
   *
   * @default 'default'
   */
  background?: "default" | "none";
  /**
   * CTA 위에 렌더링되는 악세서리 요소에요.
   */
  topAccessory?: ReactNode;
  /**
   * CTA 아래에 렌더링되는 악세서리 요소에요.
   */
  bottomAccessory?: ReactNode;
}
```

---

# FixedBottomCTA (/tds-mobile/components/BottomCTA/fixed-bottom-cta/)

export function getPreviewBox(PreviewComponent) {
return (
[Preview: VirtualRoot]
);
}

# FixedBottomCTA

`FixedBottomCTA` 컴포넌트는 화면 하단에 고정된 CTA버튼을 표현할 때 사용해요.

{getPreviewBox(Basic)}

## 사용 예제

### Double

TypeB는 버튼이 두 개가 렌더링되는 형태에요.

### 스크롤 애니메이션

`hideOnScroll` 속성을 추가하면 스크롤 시 버튼이 자동으로 숨겨지거나 나타나는 애니메이션이 적용돼요. 사용자가 아래로 스크롤할 때 버튼이 사라지고, 위로 스크롤할 때 다시 나타나요.

---

# Single (/tds-mobile/components/BottomCTA/Single/)

## BottomCTA.Single

`BottomCTA.Single`는 이 BottomCTA의 구성 요소 중 하나로, 버튼을 **하나만** 렌더링하는 간단한 형태에요.

[Preview: BottomCTA]

## 사용법

### 배경색 없애기

`BottomCTA.Single` 컴포넌트는 기본적으로 배경색이 있어요. 배경색을 없애려면 `background` prop을 `none`으로 설정하세요.

[Preview: BottomCTA]

### SafeArea의 영향 받지 않기

`hasSafeAreaPadding` prop을 `true`로 설정하면, 기기 화면 하단에 있는 SafeArea의 높이만큼 `paddingBottom`이 추가되어 버튼이 안전하게 표시돼요. 이때 웹뷰에서 user-agent로 전달된 SafeArea 정보를 `--toss-safe-area-bottom` 변수에 반영해 사용해요.

아래 코드와 같이 변수가 선언돼요. 이때 웹뷰로부터 전달받아 파싱된 값이 `--toss-safe-area-bottom` 이에요.
이때 웹뷰로부터 전달받아 파싱된 값이 `--toss-safe-area-bottom` 이에요.

```html
<style>
  --bottom-cta-padding-bottom: max(
    var(--toss-safe-area-bottom, 0px),
    env(safe-area-inset-bottom),
    20px
  );
</style>
```

### 최상단 요소 스타일 변경하기

`containerStyle` prop을 통해 최상단 요소의 스타일을 변경할 수 있어요.

> 모바일 키패드 사용시에는 opacity 혹은 bottom 값을 변경하는 것을 지양해야 해요.

### 상단/하단 요소 추가하기

`topAccessory` 와 `bottomAccessory` prop을 사용하면 상단과 하단에 요소를 추가할 수 있어요.

**Example: Accessory**

```tsx
<BottomCTA.Single
  topAccessory={<div>topAccessory</div>}
  bottomAccessory={<div>bottomAccessory</div>}
>
  여기는 설명이 들어갑니다
</BottomCTA.Single>
```

### 키보드 위에 고정하기

`fixedAboveKeyboard` prop을 `true`로 설정하면, 키보드가 활성화된 상태에서도 버튼이 키보드 위에 고정돼요. 이 설정을 통해 사용자가 키보드를 통해 입력하는 상황에서도 CTA 버튼을 쉽게 누를 수 있어요.

> 이 기능은 `BottomCTA.Double`에서는 사용할 수 없어요.

### 애니메이션 설정하기

`showAfterDelay` prop을 사용하면 지정한 시간만큼 지연된 후에 버튼이 애니메이션과 함께 나타나도록 할 수 있어요.

**Example: ShowAfterDelay**

```tsx
function ShowAfterDelay() {
  const [animation, setAnimation] = React.useState<"fade" | "scale" | "slide">(
    "fade",
  );

  return (
    <>
      <SegmentedControl
        value={animation}
        onChange={setAnimation as (v: string) => void}
      >
        <SegmentedControl.Item value="fade">fade</SegmentedControl.Item>
        <SegmentedControl.Item value="scale">scale</SegmentedControl.Item>
        <SegmentedControl.Item value="slide">slide</SegmentedControl.Item>
      </SegmentedControl>
      <BottomCTA.Single showAfterDelay={{ animation, delay: 1 }}>
        여기는 설명이 들어갑니다
      </BottomCTA.Single>
    </>
  );
}
```

### 스크롤에 따라 숨김 처리하기

`hideOnScroll` prop을 `true`로 설정하면, 사용자가 페이지를 스크롤할 때 버튼이 자동으로 숨겨져요.
이때 `hideOnScrollDistanceThreshold` prop을 사용해 버튼이 숨겨지는 스크롤 지점을 설정할 수 있어요.

## 인터페이스

**Type: TypeAProps**

```typescript
export interface TypeAProps {
  /**
   * 초기 등장 애니메이션을 정의해요.
   */
  showAfterDelay?: {
    /**
     * 등장 애니메이션 타입을 정의해요.
     */
    animation: "slide" | "fade" | "scale";
    /**
     * 초 단위로 등장 애니메이션 지연 시간을 정의해요.
     */
    delay: number;
  };
  /**
   * CTA가 숨거나 등장할 때 애니메이션을 적용해요.
   * 초기 등장 애니메이션이 아니에요.
   *
   * @default false
   */
  show?: boolean;
  /**
   * 스크롤에 따라 CTA를 숨길지 결정해요.
   * true로 설정하면 CTA가 아래로 스크롤될 때 숨고, 위로 스크롤될 때 나타나요.
   *
   * @default false
   */
  hideOnScroll?: boolean;
  /**
   * hideOnScroll이 true일 때 넘겨준 값만큼 스크롤이 이동해야 발생해요.
   * 이 때 단위는 px이에요.
   *
   * @default 1
   */
  hideOnScrollDistanceThreshold?: number;
  /**
   * 하단 `safeArea`만큼의 `paddingBottom`을 갖게 할지를 결정해요.
   * `hasPaddingBottom`이 `false`라면, `hasSafeAreaPadding` 값에 관계없이 `paddingBottom`이 0px로 고정돼요.
   * `hasPaddingBottom`이 `true`이고 `hasSafeAreaPadding`이 `false`라면 `paddingBottom`은 20px로 설정돼요.
   *
   * @default true
   */
  hasSafeAreaPadding?: boolean;
  /**
   * false 로 설정하게 될 경우 CTA의 paddingBottom 을 0으로 설정해요.
   *
   * @default true
   */
  hasPaddingBottom?: boolean;
  /**
   * `takeSpace`는 컴포넌트가 화면에 고정된 상태에서 레이아웃 공간을 차지할지를 결정해요.
   * `true`라면 `FixedBottomCTA`와 유사하게 고정된 상태에서 공간을 차지하고,
   * `false`라면 화면 하단에 고정되지만 레이아웃에 영향을 미치지 않아요.
   * `fixed`가 `true`일 때는 기본값이 `true`에요.
   */
  takeSpace?: boolean;
  /**
   * 화면 최하단에 고정시킬지 결정해요.
   * BottomCTA 에서 fixed 를 주면, FixedBottomCTA 를 사용하는 것과 동일해요.
   */
  fixed?: boolean;
  /**
   * 모바일 키보드가 표시될 때 사용을 권장하지 않는 스타일을 설정하는 객체에요.
   * 모바일 키보드가 있다면 `opacity`와 `bottom` 속성 사용을 피하는 것을 권장해요.
   */
  containerStyle?: React.CSSProperties;
  /**
   * 컨테이너 요소에 대한 ref에요.
   */
  containerRef?: Ref<HTMLDivElement>;

  /**
   * 버튼 내부에 렌더링되는 컨텐츠에요.
   */
  children: ReactNode;
  /**
   * `none`으로 주면 gradient와 배경색이 없어져요.
   *
   * @default 'default'
   */
  background?: "default" | "none";
  /**
   * CTA 위에 렌더링되는 악세서리 요소에요.
   */
  topAccessory?: ReactNode;
  /**
   * CTA 아래에 렌더링되는 악세서리 요소에요.
   */
  bottomAccessory?: ReactNode;
  /**
   * BottomSheet.CTA 버튼이 키보드 위에 고정되어야 할 때 사용해요.
   */
  fixedAboveKeyboard?: boolean;
}
```

---

# Bubble (/tds-mobile/components/bubble/)

# Bubble

`Bubble` 컴포넌트는 대화형 UI에서 메시지를 표시하는 데 사용돼요. 이 컴포넌트를 사용하면 사용자의 메시지와 상대방의 메시지를 색상과 말풍선 모양으로 구분할 수 있어요.

[Preview: Basic]

## 사용법

### 메시지의 주체 구분하기

`Bubble` 컴포넌트의 주체가 나, 상대방인 경우를 구분할 수 있어요. `background` 속성을 통해 `blue`라면 나, `grey`라면 상대방이 주체예요.

**Example: ColorVariantBubble**

```tsx
<div style={{ display: "flex", flexDirection: "column", gap: "8px" }}>
  <div style={{ display: "flex", justifyContent: "flex-start" }}>
    <Bubble background="grey" withTail>
      Hello
    </Bubble>
  </div>
  <div style={{ display: "flex", justifyContent: "flex-end" }}>
    <Bubble background="blue" withTail>
      Hello
    </Bubble>
  </div>
  <div style={{ display: "flex", justifyContent: "flex-start" }}>
    <Bubble background="grey" withTail>
      How are you?
    </Bubble>
  </div>
</div>
```

### 말풍선에 꼬리 추가할지 선택하기

말풍선 꼬리를 추가할지 선택할 수 있어요. 꼬리가 있는 경우에는 `grey(상대방)`일 때 항상 왼쪽, `blue(나)`일 때 항상 오른쪽이에요.

**Example: NoTailBubble**

```tsx
<div style={{ display: "flex", flexDirection: "column", gap: "8px" }}>
  <div style={{ display: "flex", justifyContent: "flex-start" }}>
    <Bubble background="grey" withTail={false}>
      Hello
    </Bubble>
  </div>
  <div style={{ display: "flex", justifyContent: "flex-start" }}>
    <Bubble background="grey" withTail>
      How are you?
    </Bubble>
  </div>
  <div style={{ display: "flex", justifyContent: "flex-end" }}>
    <Bubble background="blue" withTail={false}>
      Hello
    </Bubble>
  </div>
  <div style={{ display: "flex", justifyContent: "flex-end" }}>
    <Bubble background="blue" withTail>
      I am fine.
    </Bubble>
  </div>
</div>
```

## 인터페이스

`BubbleProps` 인터페이스는 `HTMLAttributes<HTMLDivElement>`를 확장하여, HTML `div` 요소에서 사용할 수 있는 모든 속성을 포함하고 있어요.

**Type: BubbleProps**

```typescript
export interface BubbleProps {
  /**
   * `Bubble` 컴포넌트의 배경 색상이에요. `blue` 또는 `grey` 중 하나를 선택할 수 있어요.
   *
   * `blue`는 나이고, `grey`는 상대방이에요.
   */
  background: "blue" | "grey";

  /**
   * `Bubble` 컴포넌트에 꼬리가 있는지 여부를 결정해요. 기본값은 `true`이에요.
   *
   * @default true
   */
  withTail?: boolean;

  /**
   * `Bubble` 컴포넌트 내부에 들어갈 자식 요소예요.
   *
   * 보통의 경우에는 `string`을 사용해요. 로티 등 다양하게 활용할 수 있어요.
   */
  children?: ReactNode;
}
```

---

# Button (/tds-mobile/components/button/)

# Button

[Image: Button thumbnail - button/Thumbnail-Button.png]

`Button` 컴포넌트는 사용자가 어떤 액션을 트리거하거나 이벤트를 실행할 때 사용해요. 버튼은 기본적인 UI 요소로, 폼 제출, 다이얼로그 열기, 작업 취소, 삭제와 같은 다양한 액션을 처리하는 데 사용해요.

[Preview: Button]

## 사용 예제

### 크기 조정하기

`Button` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. `small`, `medium`, `large`, `xlarge` 중 하나를 선택할 수 있어요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Button size="small">Small</Button>
  <Button size="medium">Medium</Button>
  <Button size="large">Large</Button>
  <Button size="xlarge">XLarge</Button>
</div>
```

### 스타일

버튼의 스타일을 설정하려면 `variant` 속성을 사용하세요. 선택 할 수 있는 값에는 `fill`과 `weak`이 있어요.

#### fill

`fill` variant는 채도가 높아 시각적으로 강렬하고 눈에 띄는 디자인이라 주요 액션을 강조하는 데 적합해요. 사용자가 버튼을 즉시 인지하고 상호작용할 수 있도록 도와줘요.

**Example: FillColors**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Button color="primary" variant="fill">
    Primary
  </Button>
  <Button color="dark" variant="fill">
    Dark
  </Button>
  <Button color="danger" variant="fill">
    Danger
  </Button>
  <div style={{ background: colors.blue500, padding: 8 }}>
    <Button color="light" variant="fill">
      Light
    </Button>
  </div>
</div>
```

#### weak

`weak` variant는 채도가 낮아 시각적으로 덜 강렬하며 부드럽고 조용한 느낌을 줘요. 그래서 덜 중요한 액션이나 보조적인 버튼에 적합해요. 이 variant를 사용하면 주요 액션과 보조 액션을 명확히 구분할 수 있죠. `weak` variant의 버튼은 반투명하게 디자인되어 배경색이 살짝 드러나는 모습이에요.

**Example: WeakColors**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Button color="primary" variant="weak">
    Primary
  </Button>
  <Button color="dark" variant="weak">
    Dark
  </Button>
  <Button color="danger" variant="weak">
    Danger
  </Button>
  <div style={{ background: colors.blue500, padding: 8 }}>
    <Button color="light" variant="weak">
      Light
    </Button>
  </div>
</div>
```

### 형태

버튼의 형태를 변경하려면 `display` 속성을 사용하세요. 선택할 수 있는 값에는 `inline`, `block`, `full`이 있어요.

- `inline`: 다른 요소와 나란히 배치돼요.
- `block`: 버튼이 줄바꿈되어 화면 너비에 맞게 확장돼요.
- `full`: 버튼이 부모 요소의 전체 너비를 차지해요.

[Image: Button display exmplae - button/button-display.png]

```tsx copy
<Button display="inline">Inline</Button>
<Button display="block">Block</Button>
<Button display="full">Full</Button>
```

### 로딩

`loading` 속성을 사용해 버튼의 로딩 상태를 나타낼 수 있어요. 로딩 중에는 3개의 인디케이터가 순차적으로 움직이며, 버튼의 너비는 변하지 않아요.

**Example: Loadings**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Button color="primary" loading>
    Primary
  </Button>
  <Button color="dark" loading>
    Dark
  </Button>
  <Button color="danger" loading>
    Danger
  </Button>
</div>
```

### 비활성화

버튼을 비활성화하려면 `disabled` 속성을 사용하세요. 비활성화된 버튼은 사용자가 클릭할 수 없고, 시각적으로도 비활성화된 상태임을 나타내요.

**Example: Disables**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Button color="primary" disabled>
    Primary
  </Button>
  <Button color="dark" disabled>
    Dark
  </Button>
  <Button color="danger" disabled>
    Danger
  </Button>
</div>
```

### 로딩과 비활성화

`loading`과 `disabled` 속성을 동시에 사용할 수 있어요. 두 가지 속성을 모두 사용하면 버튼은 로딩 중이면서 비활성화된 상태로 표시돼요.

**Example: LoadingAndDisables**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <Button color="primary" loading disabled>
    Primary
  </Button>
  <Button color="dark" loading disabled>
    Dark
  </Button>
  <Button color="danger" loading disabled>
    Danger
  </Button>
</div>
```

### 색상 업데이트

`Button` 컴포넌트의 색상을 업데이트하기 위해 CSS 변수를 활용할 수 있어요.

- `--button-color`: 버튼 텍스트의 색상을 지정해요.
- `--button-background-color`: 버튼의 배경색을 지정해요.
- `--button-disabled-opacity-color`: 비활성화 상태일 때 배경색의 투명도를 조절해요.
- `--button-disabled-text-opacity`: 비활성화 상태일 때 텍스트의 투명도를 조절해요.
- `--button-gradient-color`: 로딩 상태일 때 표시되는 그라데이션 효과의 색상을 지정해요.
- `--button-loader-color`: 로딩 상태일 때 표시되는 로더의 색상을 지정해요.
- `--button-loading-background-color`: 로딩 상태일 때 버튼 위에 표시되는 딤(dim) 레이어의 색상을 지정해요.
- `--button-loading-opacity`: 로딩 상태일 때 딤(dim) 레이어의 투명도를 조절해요.
- `--button-pressed-background-color`: 버튼이 눌렸을 때 표시되는 딤(dim) 레이어의 색상을 지정해요.
- `--button-pressed-opacity`: 버튼이 눌렸을 때 딤(dim) 레이어의 투명도를 조절해요.

**Example: UpdateBackgroundColor**

```tsx
<Button
  style={
    {
      "--button-color": "white",
      "--button-background-color": "red",
    } as CSSProperties
  }
>
  응모하기
</Button>
```

## 접근성

Button 컴포넌트는 다음과 같이 기본적인 접근성을 제공해요. 덕분에 별도의 설정 없이도 기본적으로 사용자의 접근성을 고려한 형태의 `Button` 컴포넌트를 제공할 수 있어요.

| 속성       | 접근성 효과                                     | 설명                                                                        |
| ---------- | ----------------------------------------------- | --------------------------------------------------------------------------- |
| `button`   | 스크린 리더에서 "버튼"으로 인식해요.            | 버튼 역할을 명확히 전달해서 사용자가 상호작용 가능하다는 것을 알 수 있어요. |
| `disabled` | 비활성화된 상태를 스크린 리더에서 읽어줘요.     | 버튼이 비활성화되어 상호작용할 수 없다는 정보를 스크린 리더로 알려줘요.     |
| `loading`  | `aria-busy` 속성을 사용해 로딩 중임을 알려줘요. | 로딩 상태일 때, 스크린 리더가 "작업 중" 상태를 전달해 줘요.                 |

```tsx
<Button as="button" htmlType="submit">Submit</Button>
<Button as="a" href="https://example.com">Link</Button>
```

### 추가로 지원해야 하는 접근성

개발자가 접근성을 고려해서 다음 내용을 추가로 작업해야 할 때도 있어요. 예를 들어 아이콘 버튼을 사용하거나, 특정 의미를 명확히 전달하기 어려울 때는 컴포넌트에서 제공하는 기본적인 접근성으로는 충분하지 않아요.

#### 적절한 태그 추가하기

[`as`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLLinkElement/as) 속성으로 `button`이나 `a` 태그를 선택할 수 있어요.

- `button` 태그: 버튼으로 작동하고 상호작용할 수 있게 해요.
- `a` 태그: `Button` 컴포넌트를 링크로 사용할 때는 꼭 `href` 속성을 포함해서 목적을 명확히 해주세요.

```tsx
<Button as="button" htmlType="submit">Submit</Button>
<Button as="a" href="https://example.com">Link</Button>
```

#### 아이콘만 있거나 설명이 부족할 때

- 버튼에 아이콘만 있거나 텍스트로 목적을 충분히 설명하지 못할 때: `aria-label` 속성을 사용해 추가 정보를 제공하세요.
- 아이콘만 있을 때: 스크린 리더가 버튼의 기능을 알 수 없기 때문에 `aria-label`을 추가해 주세요.
- 설명이 부족할 때: 버튼의 목적이 명확하지 않을 때는 추가 설명을 넣어주세요.

```tsx
<Button aria-label="좋아요 표시"><HeartIcon /></Button>
<Button aria-label="계정 삭제 - 주의 필요" type="danger">삭제</Button>
```

#### 로딩 상태에서 추가 정보가 필요할 때

로딩 중일 때 텍스트가 없다면 `aria-label`을 사용해 어떤 작업을 처리 중인지 알려주세요.

```tsx
<Button loading aria-label="데이터 로딩 중">
  <LoadingIcon />
</Button>
```

## 인터페이스

**Type: ButtonProps**

```typescript
export interface ButtonProps {
  /**
   * `as prop`을 통해 버튼의 태그를 변경할 수 있어요. 버튼의 태그를 변경하면 버튼의 기본 속성이 변경돼요.
   *
   * @default 'button'
   *
   */
  as?: "button" | "a";
  /**
   * 버튼의 컬러에 따라 버튼의 색상이 변경돼요.
   *
   * @default 'primary'
   */
  color?: "primary" | "danger" | "light" | "dark";
  /**
   * 버튼의 형태에 따라 버튼의 색상과 투명도가 변경돼요.
   *
   * @default 'fill'
   */
  variant?: "fill" | "weak";
  /**
   * 버튼의 표시 방식에 따라 버튼의 너비와 형태가 변경돼요.
   *
   * @default 'inline'
   */
  display?: "inline" | "block" | "full";
  /**
   * 버튼의 크기에 따라 버튼의 너비와 높이가 변경돼요.
   *
   * @default 'xlarge'
   */
  size?: "small" | "medium" | "large" | "xlarge";
  /**
   * true일 경우 버튼에 로딩 스피너가 표시돼요.
   */
  loading?: boolean;
  /**
   * true일 경우 버튼이 비활성화돼요.
   */
  disabled?: boolean;
  /**
   * `type` prop이 사용되어 기존 HTML 버튼 태그의 type 속성을 변경할 때 사용해요.
   */
  type?: "button" | "submit" | "reset" | undefined;
  /**
   * `style` prop이 사용되어 기존 HTML 버튼 태그의 style 속성을 변경할 때 사용해요.
   */
  htmlStyle?: CSSProperties;
}
```

---

# BarChart (/tds-mobile/components/Chart/bar-chart/)

# BarChart

`BarChart` 컴포넌트는 막대 그래프 형태로 데이터의 값을 시각화하는 도구예요.
`BarChart`를 사용하면 데이터를 막대의 높이로 표현할 수 있고, 색상을 지정하여 특정 막대를 강조 할 수 있어요.
이를 통해 사용자는 데이터의 중요도를 한눈에 파악할 수 있어요.

[Preview: Basic]

## 사용법

### 항목 구성하기

`BarChart`에 `data`를 전달하려면 아래와 같은 항목을 포함해야 해요.

- `maxValue`: `BarChart` 전체에서 최대값을 설정하는데 사용해요. 모든 `value` 값은 `maxValue`에 대한 비율로 표시돼요.
- `value`: 해당 막대의 실제 값을 나타내요. 막대의 높이는 이 값에 비례해 설정돼요.
- `label`: X축에 나타나는 레이블로, 각 막대가 나타내는 항목을 설명하는 텍스트예요.
- `barAnnotation`: 각 막대 위에 표시할 텍스트나 숫자예요. 해당 값이나 설명을 표시해 사용자가 데이터를 쉽게 이해할 수 있도록 도와줘요.
- `theme`: 해당 막대의 색상을 설정하는 속성이에요. `BarChart`에서 선택할 수 있는 색상 테마에는 `blue`, `green`, `yellow`, `orange`, `red`, `grey`, `default`가 있어요.

```tsx
<BarChart
  data={[
    { maxValue: 10, value: 6, label: "1월", barAnnotation: 6 },
    { maxValue: 10, value: 5, label: "2월", barAnnotation: 5 },
    { maxValue: 10, value: 4, label: "3월", barAnnotation: 4 },
    { maxValue: 10, value: 3, label: "4월", barAnnotation: 3 },
    { maxValue: 10, value: 2, label: "5월", barAnnotation: 2 },
    { maxValue: 10, value: 1, label: "6월", barAnnotation: 1 },
  ]}
  fill={{
    type: "all-bar",
    theme: "green",
  }}
/>
```

**Example: DataView**

```tsx

```

### 차트 스타일 지정하기

`BarChart`의 막대 스타일은 `fill`의 `type` 속성으로 설정할 수 있으며, 세 가지 타입인 `all-bar`, `single-bar`, `auto`를 지원해요.
각 타입에 따라 추가적으로 필요한 속성도 달라져요.

#### 전체 막대 색상 변경하기

`all-bar`는 모든 막대에 동일한 색상을 적용하고 싶을 때 사용하는 옵션이에요.
예를 들어, 모든 막대를 노란색으로 설정할 수 있어요. 이 경우 `theme` 속성을 이용해 적용할 색상만 지정해 주면 돼요.

**Example: AllBar**

```tsx

```

#### 하나의 항목만 강조하기

`single-bar`는 하나의 막대만 다른 색상으로 강조할 때 사용하는 옵션이에요.
강조할 막대의 인덱스를 `barIndex` 속성으로 지정해 주면 선택한 막대만 색상이 적용되어 강조돼요.

**Example: SingleBar**

```tsx

```

#### 자동으로 여러 항목 강조하기

`auto`는 여러 개의 막대를 자동으로 색상 적용하고 싶을 때 사용하는 타입이에요.
이 경우 `count` 속성을 설정해서 오른쪽부터 몇 개의 막대에 색상을 적용할지 지정할 수 있어요.
`auto` 타입의 색상 적용 순서는 오른쪽부터 `blue → green → yellow → orange → red → grey` 순서로 적용돼요.

**Example: Auto**

```tsx
function Auto() {
  const data = [
    { maxValue: 10, value: 6, label: '1월', barAnnotation: 6 },
    { maxValue: 10, value: 5, label: '2월', barAnnotation: 5 },
    { maxValue: 10, value: 4, label: '3월', barAnnotation: 4 },
    { maxValue: 10, value: 3, label: '4월', barAnnotation: 3 },
    { maxValue: 10, value: 2, label: '5월', barAnnotation: 2 },
    { maxValue: 10, value: 1, label: '6월', barAnnotation: 1 },
  ];
  return (

  );
}
```

### 높이 설정하기

차트 전체의 높이를 설정하는 속성이에요. 막대 개수에 상관없이 이 값에 따라 차트 전체 높이가 설정돼요.
막대 하나하나의 높이가 아닌, `BarChart` 컴포넌트 전체의 세로 길이를 조정할 때 사용해요.

**Example: Height**

```tsx

```

### 데이터가 많은 경우 표시하기

data의 항목 개수가 12개를 초과하면, 차트에서는 첫 번째와 마지막 항목에만 `label`과 `barAnnotation`이 표시돼요.
데이터가 많을 때 라벨이 겹쳐 보이는 것을 방지하기 위한 설정이에요.

**Example: DataSamples**

```tsx
function DataSamples() {
  const data = [
    { maxValue: 10, value: 8, label: '2012', barAnnotation: 8 },
    { maxValue: 10, value: 7, label: '2013', barAnnotation: 7 },
    { maxValue: 10, value: 6, label: '2014', barAnnotation: 6 },
    { maxValue: 10, value: 5, label: '2015', barAnnotation: 5 },
    { maxValue: 10, value: 4, label: '2016', barAnnotation: 4 },
    { maxValue: 10, value: 3, label: '2017', barAnnotation: 3 },
    { maxValue: 10, value: 2, label: '2018', barAnnotation: 2 },
    { maxValue: 10, value: 3, label: '2019', barAnnotation: 3 },
    { maxValue: 10, value: 4, label: '2020', barAnnotation: 4 },
    { maxValue: 10, value: 5, label: '2021', barAnnotation: 5 },
    { maxValue: 10, value: 6, label: '2022', barAnnotation: 6 },
    { maxValue: 10, value: 7, label: '2023', barAnnotation: 7 },
    { maxValue: 10, value: 8, label: '2024', barAnnotation: 8 },
  ];
  return (

  );
}
```

## 인터페이스

**Type: BarChartProps**

```typescript
export interface BarChartProps {
  data: "BarChartData[]";
  fill: "AllBar | SingleBar | Auto";
  /**
   * 차트 전체의 높이를 설정해요. 단위는 `px`이고, 기본값은 205예요.
   * @default 205
   */
  height?: number;
}
```

**Type: BarChartData**

```typescript
export interface BarChartData {
  /**
   * 차트에서 막대의 길이에요.
   * */
  value: number;
  /**
   * 차트에서 나타낼 최대값이에요. 설정하지 않으면 차트가 자동으로 최대값을 계산해요.
   * */
  maxValue?: number;
  /**
   * X축에 표시될 레이블이에요.
   * */
  label?: string;
  /**
   * 막대의 색상을 설정해요.
   * */
  theme?: "blue" | "green" | "yellow" | "orange" | "red" | "grey" | "default";
  /**
   * 막대 위에 표시할 텍스트나 숫자예요.
   * */
  barAnnotation?: string | number;
}
```

**Type: AllBar**

```typescript
export interface AllBar {
  /**
   * 모든 막대에 같은 색상을 적용해요.
   */
  type: "all-bar";
  /**
   * 모든 막대를 한가지 색상으로 적용해요.
   * */
  theme: "blue" | "green" | "yellow" | "orange" | "red" | "grey" | "default";
}
```

**Type: SingleBar**

```typescript
export interface SingleBar {
  /**
   * 선택한 하나의 막대에만 색상을 적용해요.
   */
  type: "single-bar";
  /**
   * 선택한 하나의 막대의 색상을 설정해요.
   * */
  theme: "blue" | "green" | "yellow" | "orange" | "red" | "grey" | "default";
  /**
   * 색상을 적용할 막대의 위치를 지정하는 인덱스에요.
   */
  barIndex: number;
}
```

**Type: Auto**

```typescript
export interface Auto {
  /**
   * 막대에 정해진 규칙으로 색상을 자동으로 지정해요.
   * blue -> green -> yellow -> orange -> red -> grey 순서로 오른쪽부터 적용돼요.
   */
  type: "auto";
  /**
   * 색상을 적용할 막대의 개수예요. 색상은 오른쪽부터 적용돼요.
   */
  count: number;
}
```

---

# Checkbox (/tds-mobile/components/checkbox/)

# Checkbox

`Checkbox` 컴포넌트는 사용자가 하나 이상의 항목을 선택할 때 사용해요. 체크된 상태와 체크되지 않은 상태를 나타내고, 여러 개의 항목을 동시에 선택할 수 있어요.

[Preview: Basic]

## 사용 예제

### 형태

`Checkbox`는 두 가지 방법으로 표현할 수 있어요.

- ``: 체크 아이콘이 원으로 감싸진 형태로 표현돼요.
- ``: 체크 아이콘이 단독으로 표현돼요.

**Example: Shapes**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}></div>
```

### 상태

#### 상태를 외부에서 관리하는 방식

`Checkbox`의 상태를 외부에서 관리하려면 `checked`와 `onCheckedChange` 속성을 함께 사용하세요. 이렇게 하면 체크박스가 선택되었는지 아닌지를 외부에서 직접 관리할 수 있어요.

**Example: Controlled**

```tsx
function Controlled() {
  const [checked, setChecked] = React.useState(true);

  return <div style={{ display: "flex", alignItems: "center", gap: 8 }}></div>;
}
```

#### 상태를 내부에서 관리하는 방식

`Checkbox`의 상태를 내부에서 자동으로 관리하려면 `defaultChecked` 속성을 사용하세요. 이 속성은 체크박스가 처음 화면에 표시될 때 선택 상태를 정해주고, 그 후에는 컴포넌트가 스스로 상태를 관리해요. 이 방식은 상태 변화를 추적하지 않아도 될 때 유용해요.

**Example: Uncontrolled**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}></div>
```

### 크기 조정하기

`Checkbox`의 크기를 변경하려면 `size` 속성을 사용하세요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}></div>
```

### 비활성화하기

`Checkbox`를 비활성화하려면 `disabled` 속성을 사용하세요. 비활성화된 `Checkbox`를 클릭하면 선택 상태가 바뀌지 않고, 좌우로 흔들리는 애니메이션이 나타나요.

**Example: Disables**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}></div>
```

### 라디오 버튼으로 활용하기

`Checkbox`를 라디오 버튼으로 활용하려면 `inputType` 속성에 `'radio'`를 넣어주세요. 여러 개의 항목 중 하나만을 선택해야할 때 유용해요.

**Example: Radios**

```tsx
function Radios() {
  const [checked, setChecked] = React.useState<null | string>(null);

  return (
    <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
      <Checkbox.Circle
        inputType="radio"
        value="1"
        checked={checked === "1"}
        onChange={(e) => setChecked(e.target.value)}
      />
      <Checkbox.Circle
        inputType="radio"
        value="2"
        checked={checked === "2"}
        onChange={(e) => setChecked(e.target.value)}
      />
      <Checkbox.Circle
        inputType="radio"
        value="3"
        checked={checked === "3"}
        onChange={(e) => setChecked(e.target.value)}
      />
    </div>
  );
}
```

## 접근성

`Checkbox` 컴포넌트는 기본적으로 접근성을 지원하는 여러 속성을 포함하고 있어요. 이 속성들은 스크린 리더 사용자들이 컴포넌트를 명확하게 이해하고 상호작용할 수 있도록 도와줘요.

### 기본 접근성 지원

다음 속성이 있어서 다른 설정 없이도 기본적으로 사용자의 접근성을 고려한 `Checkbox` 컴포넌트를 제공할 수 있어요.

| 속성                                | 접근성 효과                                              | 설명                                                                                   |
| ----------------------------------- | -------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `role="checkbox"` 및 `tabindex="0"` | 스크린 리더에서 "체크박스"로 인식해요.                   | 요소의 역할을 명확히 전달해요.                                                         |
| `aria-checked`                      | 현재 체크 상태를 스크린 리더에서 알려줘요.               | 체크박스의 상태에 따라 `aria-checked` 속성이 자동으로 업데이트 돼요.                   |
| `aria-disabled="true"`              | 체크박스가 비활성화된 상태임을 스크린 리더에서 알려줘요. | 비활성화된 체크박스에 자동으로 추가되어 사용자가 상호작용할 수 없다는 정보를 전달해요. |

```jsx
<div role="checkbox" tabindex="0" aria-checked="false"></div>
```

`Checkbox` 컴포넌트는 `<input type="checkbox" />` 요소를 포함하고 있지만, 이 요소는 화면에 보이지 않아요.  
대신 시각적으로 보이는 커스텀 체크박스 요소에 `role="checkbox"`와 `aria-checked` 속성이 적용되어 있어, 스크린 리더 사용자에게 올바른 정보를 전달할 수 있어요.

### 개발자가 추가로 지원해야 하는 접근성

#### 필수로 제공해야 하는 aria-label

`Checkbox` 컴포넌트에서는 `aria-label` 속성을 필수적으로 제공해서 체크박스의 목적을 명확히 설명해야 합니다. 커스텀 체크박스와 레이블이 별도의 요소로 구현되어 있기 때문이에요. 이 속성을 사용해서 스크린 리더 사용자는 체크박스의 의미를 정확히 이해할 수 있어요.

```jsx
<Checkbox.Circle
  checked={checked}
  onCheckedChange={setChecked}
  aria-label="이용약관 동의" // 개발자가 필수로 제공해야 합니다
/>
```

주의할 점은 `aria-label`을 작성할 때 "체크박스"라는 요소 유형은 적지 않도록 해야 해요. 스크린 리더가 이미 "체크박스"라고 읽어주기 때문에 중복된 정보를 제공하지 않도록 주의해야 합니다.
이러한 접근성 고려사항을 적용하면, 더욱 포괄적이고 사용하기 쉬운 체크박스 컴포넌트를 만들 수 있어요. 개발자가 `aria-label`을 필수로 제공함으로써, 모든 사용자가 체크박스의 목적을 명확히 이해할 수 있게 되어 웹 접근성이 크게 향상됩니다.

## 인터페이스

**Type: CheckboxProps**

```typescript
export interface CheckboxProps {
  /**
   * input 태그의 `type` 속성을 결정해요.
   * @default 'checkbox'
   */
  inputType?: "checkbox" | "radio";
  /**
   * `Checkbox` 컴포넌트의 크기를 결정해요.
   * @default 24
   */
  size?: number;
  /**
   * 이 값이 `true`일 때 해당 `Checkbox`가 선택된 상태로 표현돼요. 주로 `Checkbox` 컴포넌트의 상태를 컴포넌트 외부에서 관리할 때, `onCheckedChange` 속성과 함께 사용해요.
   */
  checked?: boolean;
  /**
   * `Checkbox` 컴포넌트의 선택 상태가 바뀔 때 실행되는 함수예요.
   */
  onCheckedChange?: (checked: boolean) => void;
  /**
   * `Checkbox` 컴포넌트의 상태를 컴포넌트 내부에서 관리할 때, 초기 선택 상태를 지정해요.
   */
  defaultChecked?: boolean;
  /**
   * 이 값이 `true`일 때 `Checkbox` 컴포넌트가 비활성화돼요.
   */
  disabled?: boolean;
}
```

---

# AlertDialog (/tds-mobile/components/Dialog/alert-dialog/)

# AlertDialog

`AlertDialog` 컴포넌트는 사용자에게 중요한 정보를 전달하고 단일 확인 버튼을 사용해서 알림을 닫을 수 있는 인터페이스를 제공해요. 주로 작업 완료 알림이나 상태 변경 알림 등 사용자에게 피드백을 제공할 때 사용해요.

[Preview: Basic]

## 사용 예제

### 기본 사용법

`AlertDialog` 컴포넌트의 기본적인 구성은 제목(`title`), 설명(`description`), 확인 버튼(`alertButton`)으로 이루어져 있어요. `open` 상태와 `onClose` 핸들러를 함께 사용하여 `AlertDialog` 컴포넌트의 표시 여부를 제어할 수 있어요.

**Example: Basic**

```tsx
function Basic() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>기본 알림 다이얼로그</Button>
      <AlertDialog
        open={open}
        title={
          <AlertDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </AlertDialog.Title>
        }
        description={
          <AlertDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한 서비스를 만들게요.\n"}
          </AlertDialog.Description>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setOpen(false)}>
            확인
          </AlertDialog.AlertButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

### 외부 딤 클릭 제어하기

`closeOnDimmerClick` 속성을 사용해서 `AlertDialog` 컴포넌트의 바깥 영역을 클릭할 때의 동작을 제어할 수 있어요. 기본값은 `true`이며, `false`로 설정하면 외부 클릭으로 `AlertDialog` 컴포넌트가 닫히지 않고, Wiggle 애니메이션을 보여줘요.

**Example: WithWiggle**

```tsx
function WithWiggle() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>딤 누르면 위글</Button>
      <AlertDialog
        open={open}
        title={
          <AlertDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </AlertDialog.Title>
        }
        description={
          <AlertDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한\n서비스를 만들게요."}
          </AlertDialog.Description>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setOpen(false)}>
            확인
          </AlertDialog.AlertButton>
        }
        onClose={() => setOpen(false)}
        closeOnDimmerClick={false}
      />
    </>
  );
}
```

### 긴 콘텐츠 처리하기

`AlertDialog` 컴포넌트는 다양한 길이의 콘텐츠를 자연스럽게 표시할 수 있어요.

#### 긴 제목 사용하기

제목이 길어도 자연스럽게 줄 바꿈 되어 표시돼요.

**Example: LongTitle**

```tsx
function LongTitle() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>긴 제목</Button>
      <AlertDialog
        open={open}
        title={
          <AlertDialog.Title>
            {
              "30글자이상의엄청긴제목30글자이상의엄청긴제목30글자이상의엄청긴제목"
            }
          </AlertDialog.Title>
        }
        description={
          <AlertDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한\n서비스를 만들게요."}
          </AlertDialog.Description>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setOpen(false)}>
            확인
          </AlertDialog.AlertButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

#### 긴 설명 사용하기

설명이 길 때 스크롤이 자동으로 생성되어 모든 내용을 확인할 수 있어요.

**Example: LongDescription**

```tsx
function LongDescription() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>긴 설명</Button>
      <AlertDialog
        open={open}
        title={
          <AlertDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </AlertDialog.Title>
        }
        description={
          <AlertDialog.Description>
            {`소중한 의견을 바탕으로 더 간편한 서비스를 만들게요.\n`.repeat(30)}
          </AlertDialog.Description>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setOpen(false)}>
            확인
          </AlertDialog.AlertButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

#### 긴 버튼 텍스트(레이블) 사용하기

버튼의 텍스트가 길어도 레이아웃이 깨지지 않고 자연스럽게 표시돼요.

**Example: LongLabel**

```tsx
function LongLabel() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>긴 레이블</Button>
      <AlertDialog
        open={open}
        title={
          <AlertDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </AlertDialog.Title>
        }
        description={
          <AlertDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한\n서비스를 만들게요."}
          </AlertDialog.Description>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setOpen(false)}>
            {
              "30글자이상의엄청긴레이블30글자이상의엄청긴레이블30글자이상의엄청긴레이블"
            }
          </AlertDialog.AlertButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

### 설명이 없는 `AlertDialog` 컴포넌트

간단한 알림일 때는 제목과 버튼만으로도 구성할 수 있어요.

**Example: WithoutDescription**

```tsx
function WithoutDescription() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>설명 없는 다이얼로그</Button>
      <AlertDialog
        open={open}
        title={
          <AlertDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </AlertDialog.Title>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setOpen(false)}>
            확인
          </AlertDialog.AlertButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

#### 특정 DOM 요소에 렌더링하기

`AlertDialog` 컴포넌트는 기본적으로 `document.body`에 렌더링이 되지만, `portalContainer` 속성을 사용하면 렌더링 위치를 변경할 수 있어요. 이는 특히 `z-index` 관련 이슈나 특별한 레이아웃 요구사항이 있을 때 유용해요.

**Example: PortalContainer**

```tsx
function PortalContainer() {
  const [isOpen, setIsOpen] = React.useState(false);
  const containerRef = React.useRef<HTMLDivElement>(null);

  return (
    <div style={{ display: "flex", flexDirection: "column", gap: "16px" }}>
      {/* 다이얼로그가 렌더링될 컨테이너 */}
      <div
        ref={containerRef}
        style={{
          position: "relative",
          padding: "16px",
          border: "2px dashed #E5E5EC",
          borderRadius: "8px",
          minHeight: "100px",
        }}
      >
        <div style={{ color: "#98989F" }}>
          다이얼로그가 이 영역에 렌더링돼요.
        </div>
      </div>

      {/* 버튼은 별도의 영역에 위치 */}
      <div>
        <Button onClick={() => setIsOpen(true)}>다이얼로그 열기</Button>
        <p style={{ marginTop: "8px", color: "#98989F", fontSize: "14px" }}>
          👆 버튼은 다른 영역에 있지만, 다이얼로그는 위의 점선 영역에 그려져요.
        </p>
      </div>

      <AlertDialog
        open={isOpen}
        portalContainer={containerRef.current}
        title={
          <AlertDialog.Title>
            특정 컨테이너에 렌더링되는 다이얼로그
          </AlertDialog.Title>
        }
        description={
          <AlertDialog.Description>
            이 다이얼로그는 DOM 구조상 상단의 점선 영역에 렌더링 되지만,
            시각적으로는 여전히 전체 화면을 덮어요. 일반적으로 document.body에
            렌더링되는 것과 달리, 지정된 컨테이너의 자식 요소로 마운트돼요.
          </AlertDialog.Description>
        }
        alertButton={
          <AlertDialog.AlertButton onClick={() => setIsOpen(false)}>
            확인
          </AlertDialog.AlertButton>
        }
        onClose={() => setIsOpen(false)}
      />
    </div>
  );
}
```

## 인터페이스

**Type: AlertDialogProps**

```typescript
export interface AlertDialogProps {
  /**
   * `AlertDialog` 컴포넌트의 표시 여부를 결정해요.
   *
   * `true`일 때는 `AlertDialog` 컴포넌트가 화면에 표시되고, `false`일 때는 `AlertDialog` 컴포넌트가 숨겨져요.
   */
  open?: boolean;

  /**
   * `AlertDialog` 컴포넌트의 제목이에요.
   */
  title?: ReactNode;

  /**
   * `AlertDialog` 컴포넌트의 내용을 설명하는 텍스트나 컴포넌트를 나타낼 수 있어요.
   */
  description?: ReactNode;

  /**
   * `AlertDialog` 컴포넌트의 확인 버튼이에요.
   */
  alertButton?: ReactNode;

  /**
   * 배경을 클릭할 때 `AlertDialog` 컴포넌트를 닫을지 여부를 설정해요.
   *
   * `true`로 설정하면 사용자가 `AlertDialog` 컴포넌트 외부를 클릭했을 때 `AlertDialog` 컴포넌트가 닫혀요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * 뒤로가기 이벤트가 발생했을 때 `AlertDialog` 컴포넌트를 닫을지 여부를 결정해요.
   *
   * `true`로 설정하면 사용자가 뒤로가기를 눌렀을 때 `AlertDialog` 컴포넌트가 닫혀요.
   *
   * @default true
   */
  closeOnBackEvent?: boolean;

  /**
   * `AlertDialog` 컴포넌트가 닫힐 때 호출되는 콜백 함수에요.
   *
   * `closeOnDimmerClick`이 `true`여도 `onClose`에 함수를 전달하지 않으면 `AlertDialog` 컴포넌트가 닫히지 않아요.
   * `AlertDialog` 컴포넌트를 닫으려면 반드시 `onClose` 함수를 전달해야 해요.
   */
  onClose?: () => void;

  /**
   * `AlertDialog` 컴포넌트가 완전히 열린 후 호출되는 콜백 함수에요.
   *
   * `AlertDialog` 컴포넌트가 열리는 애니메이션이 완료된 후에 호출돼요.
   */
  onEntered?: () => void;

  /**
   * `AlertDialog` 컴포넌트가 완전히 닫힌 후 호출되는 콜백 함수에요.
   *
   * `AlertDialog` 컴포넌트가 닫히는 애니메이션이 완료된 후에 호출돼요.
   */
  onExited?: () => void;

  /**
   * `AlertDialog` 컴포넌트가 렌더링될 컨테이너를 지정해요.
   *
   * `portalContainer` 속성을 사용하면 `AlertDialog` 컴포넌트가 렌더링될 DOM 요소를 지정할 수 있어요. 기본적으로는 `document.body`에 렌더링 되지만, 특정 DOM 요소를 지정하여 렌더링 위치를 변경할 수 있어요. 이는 특히 `z-index` 관련 이슈나 특별한 레이아웃 요구사항이 있을 때 유용해요.
   *
   * @default document.body
   */
  portalContainer?: HTMLElement | null;
}
```

**Type: AlertDialogTitleProps**

```typescript
export interface AlertDialogTitleProps {
  /**
   * `AlertDialog` 컴포넌트 제목의 HTML 태그를 지정해요.
   *
   * @default 'h3'
   */
  as?: string;

  /**
   * `AlertDialog` 컴포넌트 제목의 색상을 지정해요.
   * 기본적으로 `adaptive.grey800` 색상이 사용되며, 다른 색상으로 변경할 수 있어요.
   *
   * @default adaptive.grey800
   */
  color?: string;

  /**
   * 제목의 타이포그래피를 지정해요.
   * 기본적으로 `t4` 타이포그래피가 적용돼요.
   *
   * @default 't4'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";

  /**
   * 제목의 글꼴 두께를 지정해요.
   * 기본적으로 `bold` 두께가 적용돼요.
   *
   * @default 'bold'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: AlertDialogDescriptionProps**

```typescript
export interface AlertDialogDescriptionProps {
  /**
   * `AlertDialog` 컴포넌트 설명의 HTML 태그를 지정해요.
   * 기본적으로 `h3` 태그로 렌더링돼요.
   *
   * @default 'h3'
   */
  as?: string;

  /**
   * 설명의 색상을 지정해요.
   * 기본적으로 `adaptive.grey600` 색상이 적용돼요.
   *
   * @default adaptive.grey600
   */
  color?: string;

  /**
   * 설명의 타이포그래피를 지정해요.
   * 기본적으로 `t6` 타이포그래피가 적용돼요.
   *
   * @default 't6'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";

  /**
   * 설명의 글꼴 두께를 지정해요.
   * 기본적으로 `medium` 두께가 적용돼요.
   *
   * @default 'medium'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: AlertDialogAlertButtonProps**

```typescript
export interface AlertDialogAlertButtonProps {
  /**
   * 텍스트 버튼의 사이즈를 결정해요.
   * @default 'medium'
   */
  size?: "xsmall" | "small" | "medium" | "large" | "xlarge" | "xxlarge";
  /**
   * 버튼의 색상을 지정해요.
   * 기본적으로 `colors.blue500` 색상이 적용돼요.
   *
   * @default colors.blue500
   */
  color?: string;

  /**
   * 버튼의 글꼴 두께를 지정해요.
   * 기본적으로 `bold` 두께가 적용돼요.
   *
   * @default 'bold'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";

  /**
   * 버튼의 변형을 지정해요.
   * 'arrow', 'underline', 'clear' 중 하나를 선택할 수 있어요.
   */
  variant?: "arrow" | "underline" | "clear";
}
```

---

# ConfirmDialog (/tds-mobile/components/Dialog/confirm-dialog/)

# ConfirmDialog

`ConfirmDialog` 컴포넌트는 사용자의 액션이나 선택이 필요한 상황에서 사용되는 인터페이스를 제공해요. 확인과 취소, 두 개의 버튼을 통해 사용자가 명확한 선택을 할 수 있도록 도와줘요.

[Preview: Basic]

## 사용 예제

### 기본 사용법

`ConfirmDialog` 컴포넌트의 기본적인 구성은 제목(`title`), 설명(`description`), 취소 버튼(`cancelButton`), 확인 버튼(`confirmButton`)으로 이루어져 있어요. `open`상태와`onClose`핸들러를 함께 사용하여 `ConfirmDialog` 컴포넌트의 표시 여부를 제어할 수 있어요.

**Example: Basic**

```tsx
function Basic() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>기본 확인 다이얼로그</Button>
      <ConfirmDialog
        open={open}
        title={
          <ConfirmDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </ConfirmDialog.Title>
        }
        description={
          <ConfirmDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한\n서비스를 만들게요."}
          </ConfirmDialog.Description>
        }
        cancelButton={
          <ConfirmDialog.CancelButton onClick={() => setOpen(false)}>
            아니오
          </ConfirmDialog.CancelButton>
        }
        confirmButton={
          <ConfirmDialog.ConfirmButton onClick={() => setOpen(false)}>
            예
          </ConfirmDialog.ConfirmButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

### 외부 딤 클릭 제어하기

`closeOnDimmerClick` 속성을 통해 `ConfirmDialog` 컴포넌트 외부(딤) 영역 클릭 시의 동작을 제어할 수 있어요. 기본값은 `true`이며, `false`로 설정하면 외부 클릭으로 `ConfirmDialog` 컴포넌트가 닫히지 않고, Wiggle 애니메이션을 보여줘요.

**Example: WithWiggle**

```tsx
function WithWiggle() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>딤 누르면 위글</Button>
      <ConfirmDialog
        open={open}
        title={
          <ConfirmDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </ConfirmDialog.Title>
        }
        description={
          <ConfirmDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한 서비스를 만들게요.\n"}
          </ConfirmDialog.Description>
        }
        cancelButton={
          <ConfirmDialog.CancelButton onClick={() => setOpen(false)}>
            아니오
          </ConfirmDialog.CancelButton>
        }
        confirmButton={
          <ConfirmDialog.ConfirmButton onClick={() => setOpen(false)}>
            예
          </ConfirmDialog.ConfirmButton>
        }
        onClose={() => setOpen(false)}
        closeOnDimmerClick={false}
      />
    </>
  );
}
```

### 긴 콘텐츠 처리하기

`ConfirmDialog` 컴포넌트는 다양한 길이의 콘텐츠를 자연스럽게 표시할 수 있어요.

#### 긴 설명 사용하기

설명이 길 경우 스크롤이 자동으로 생성되어 모든 내용을 확인할 수 있어요.

**Example: LongDescription**

```tsx
function LongDescription() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>긴 설명</Button>
      <ConfirmDialog
        open={open}
        title={
          <ConfirmDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </ConfirmDialog.Title>
        }
        description={
          <ConfirmDialog.Description>
            {`소중한 의견을 바탕으로 더 간편한\n서비스를 만들게요.`.repeat(30)}
          </ConfirmDialog.Description>
        }
        cancelButton={
          <ConfirmDialog.CancelButton onClick={() => setOpen(false)}>
            아니오
          </ConfirmDialog.CancelButton>
        }
        confirmButton={
          <ConfirmDialog.ConfirmButton onClick={() => setOpen(false)}>
            예
          </ConfirmDialog.ConfirmButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

#### 긴 버튼 텍스트 사용하기

버튼의 텍스트가 길어지면 버튼의 레이아웃이 자동으로 조정돼요. 버튼의 텍스트가 짧을 때는 가로로 나란히 배치되지만, 텍스트가 길어지면 세로로 쌓이면서 각 버튼이 전체 너비를 사용해요.

**Example: LongButtons**

```tsx
function LongButtons() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>긴 버튼</Button>
      <ConfirmDialog
        open={open}
        title={
          <ConfirmDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </ConfirmDialog.Title>
        }
        description={
          <ConfirmDialog.Description>
            {"소중한 의견을 바탕으로 더 간편한\n서비스를 만들게요."}
          </ConfirmDialog.Description>
        }
        cancelButton={
          <ConfirmDialog.CancelButton onClick={() => setOpen(false)}>
            아니오, 취소해주세요
          </ConfirmDialog.CancelButton>
        }
        confirmButton={
          <ConfirmDialog.ConfirmButton onClick={() => setOpen(false)}>
            예, 알겠습니다
          </ConfirmDialog.ConfirmButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

### 설명 없는 `ConfirmDialog` 컴포넌트

간단한 확인이 필요한 경우 제목과 버튼들만으로도 구성할 수 있어요.

**Example: WithoutDescription**

```tsx
function WithoutDescription() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>설명 없음</Button>
      <ConfirmDialog
        open={open}
        title={
          <ConfirmDialog.Title>
            {"김토스님의 의견이\n잘 전달되었어요"}
          </ConfirmDialog.Title>
        }
        cancelButton={
          <ConfirmDialog.CancelButton onClick={() => setOpen(false)}>
            아니오
          </ConfirmDialog.CancelButton>
        }
        confirmButton={
          <ConfirmDialog.ConfirmButton onClick={() => setOpen(false)}>
            예
          </ConfirmDialog.ConfirmButton>
        }
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

#### 특정 DOM 요소에 렌더링하기

`ConfirmDialog` 컴포넌트는 기본적으로 `document.body`에 렌더링이 되지만, `portalContainer` 속성을 사용하면 렌더링 위치를 변경할 수 있어요. 이는 특히 `z-index` 관련 이슈나 특별한 레이아웃 요구사항이 있을 때 유용해요.

**Example: PortalContainer**

```tsx
function PortalContainer() {
  const [isOpen, setIsOpen] = React.useState(false);
  const containerRef = React.useRef<HTMLDivElement>(null);

  return (
    <div style={{ display: "flex", flexDirection: "column", gap: "16px" }}>
      {/* 다이얼로그가 렌더링될 컨테이너 */}
      <div
        ref={containerRef}
        style={{
          position: "relative",
          padding: "16px",
          border: "2px dashed #E5E5EC",
          borderRadius: "8px",
          minHeight: "100px",
        }}
      >
        <div style={{ color: "#98989F" }}>
          다이얼로그가 이 영역에 렌더링돼요.
        </div>
      </div>

      {/* 버튼은 별도의 영역에 위치 */}
      <div>
        <Button onClick={() => setIsOpen(true)}>다이얼로그 열기</Button>
        <p style={{ marginTop: "8px", color: "#98989F", fontSize: "14px" }}>
          👆 버튼은 다른 영역에 있지만, 다이얼로그는 위의 점선 영역에 그려져요.
        </p>
      </div>

      <ConfirmDialog
        open={isOpen}
        portalContainer={containerRef.current}
        title={
          <ConfirmDialog.Title>
            특정 컨테이너에 렌더링되는 다이얼로그
          </ConfirmDialog.Title>
        }
        description={
          <ConfirmDialog.Description>
            이 다이얼로그는 DOM 구조상 상단의 점선 영역에 렌더링 되지만,
            시각적으로는 여전히 전체 화면을 덮어요. 일반적으로 document.body에
            렌더링되는 것과 달리, 지정된 컨테이너의 자식 요소로 마운트돼요.
          </ConfirmDialog.Description>
        }
        cancelButton={
          <ConfirmDialog.CancelButton onClick={() => setIsOpen(false)}>
            취소
          </ConfirmDialog.CancelButton>
        }
        confirmButton={
          <ConfirmDialog.ConfirmButton onClick={() => setIsOpen(false)}>
            확인
          </ConfirmDialog.ConfirmButton>
        }
        onClose={() => setIsOpen(false)}
      />
    </div>
  );
}
```

## 인터페이스

**Type: ConfirmDialogProps**

```typescript
export interface ConfirmDialogProps {
  /**
   * `ConfirmDialog` 컴포넌트의 표시 여부를 결정해요.
   *
   * `true`일 때는 `ConfirmDialog` 컴포넌트가 화면에 표시되고, `false`일 때는 `ConfirmDialog` 컴포넌트가 숨겨져요.
   */
  open?: boolean;

  /**
   * `ConfirmDialog` 컴포넌트의 제목이에요.
   */
  title?: ReactNode;

  /**
   * `ConfirmDialog` 컴포넌트의 내용을 설명하는 텍스트나 컴포넌트를 나타낼 수 있어요.
   */
  description?: ReactNode;

  /**
   * `ConfirmDialog` 컴포넌트의 취소 버튼이에요.
   */
  cancelButton?: ReactNode;

  /**
   * `ConfirmDialog` 컴포넌트의 확인 버튼이에요.
   */
  confirmButton?: ReactNode;

  /**
   * 딤(배경) 클릭 시 `ConfirmDialog` 컴포넌트를 닫을지 여부를 결정해요.
   *
   * `true`로 설정하면 사용자가 `ConfirmDialog` 컴포넌트 외부를 클릭했을 때 `ConfirmDialog` 컴포넌트가 닫혀요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * 뒤로가기 이벤트가 발생했을 때 `ConfirmDialog` 컴포넌트를 닫을지 여부를 결정해요.
   *
   * `true`로 설정하면 사용자가 뒤로가기를 눌렀을 때 `ConfirmDialog` 컴포넌트가 닫혀요.
   *
   * @default true
   */
  closeOnBackEvent?: boolean;

  /**
   * `ConfirmDialog` 컴포넌트가 닫힐 때 호출되는 콜백 함수에요.
   *
   * `closeOnDimmerClick`이 `true`이어도 `onClose`에 함수를 전달하지 않으면 `ConfirmDialog` 컴포넌트가 닫히지 않아요.
   * `ConfirmDialog` 컴포넌트를 닫으려면 반드시 `onClose` 함수를 전달해야 해요.
   */
  onClose?: () => void;

  /**
   * `ConfirmDialog` 컴포넌트가 완전히 열린 후 호출되는 콜백 함수에요.
   *
   * `ConfirmDialog` 컴포넌트가 열리는 애니메이션이 완료된 후에 호출돼요.
   */
  onEntered?: () => void;

  /**
   * `ConfirmDialog` 컴포넌트가 완전히 닫힌 후 호출되는 콜백 함수에요.
   *
   * `ConfirmDialog` 컴포넌트가 닫히는 애니메이션이 완료된 후에 호출돼요.
   */
  onExited?: () => void;

  /**
   * `ConfirmDialog` 컴포넌트가 렌더링될 컨테이너를 지정해요.
   *
   * `portalContainer` 속성을 사용하면 `ConfirmDialog` 컴포넌트가 렌더링될 DOM 요소를 지정할 수 있어요. 기본적으로는 `document.body`에 렌더링 되지만, 특정 DOM 요소를 지정하여 렌더링 위치를 변경할 수 있어요. 이는 특히 `z-index` 관련 이슈나 특별한 레이아웃 요구사항이 있을 때 유용해요.
   *
   * @default document.body
   */
  portalContainer?: HTMLElement | null;
}
```

**Type: ConfirmDialogTitleProps**

```typescript
export interface ConfirmDialogTitleProps {
  /**
   * `ConfirmDialog` 컴포넌트 제목의 HTML 태그를 지정해요.
   *
   * @default 'h3'
   */
  as?: string;

  /**
   * 제목의 색상을 지정해요.
   * 기본적으로 `adaptive.grey800` 색상이 사용되며, 다른 색상으로 변경할 수 있어요.
   *
   * @default adaptive.grey800
   */
  color?: string;

  /**
   * 제목의 타이포그래피를 지정해요.
   * 기본적으로 `t4` 타이포그래피가 적용돼요.
   *
   * @default 't4'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";

  /**
   * 제목의 글꼴 두께를 지정해요.
   * 기본적으로 `bold` 두께가 적용돼요.
   *
   * @default 'bold'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: ConfirmDialogDescriptionProps**

```typescript
export interface ConfirmDialogDescriptionProps {
  /**
   * 설명의 HTML 태그를 지정해요.
   * 기본적으로 `h3` 태그로 렌더링돼요.
   *
   * @default 'h3'
   */
  as?: string;

  /**
   * 설명의 색상을 지정해요.
   * 기본적으로 `adaptive.grey600` 색상이 적용돼요.
   *
   * @default adaptive.grey600
   */
  color?: string;

  /**
   * 설명의 타이포그래피를 지정해요.
   * 기본적으로 `t6` 타이포그래피가 적용돼요.
   *
   * @default 't6'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";

  /**
   * 설명의 글꼴 두께를 지정해요.
   * 기본적으로 `medium` 두께가 적용돼요.
   *
   * @default 'medium'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: ConfirmDialogCancelButtonProps**

```typescript
export interface ConfirmDialogCancelButtonProps {
  /**
   * 버튼의 타입을 지정해요.
   * 기본적으로 `dark` 타입이 적용돼요.
   *
   * @default 'dark'
   */
  type?: "primary" | "danger" | "light" | "dark";

  /**
   * 버튼의 스타일을 지정해요.
   * 기본적으로 `weak` 스타일이 적용돼요.
   *
   * @default 'weak'
   */
  style?: "fill" | "weak";

  /**
   * 버튼의 크기를 지정해요.
   * 기본적으로 `large` 크기가 적용돼요.
   *
   * @default 'large'
   */
  size?: "big" | "large" | "medium" | "tiny";
}
```

**Type: ConfirmDialogConfirmButtonProps**

```typescript
export interface ConfirmDialogConfirmButtonProps extends ButtonProps {
  /**
   * 버튼의 크기를 지정해요.
   * 기본적으로 `large` 크기가 적용돼요.
   *
   * @default 'large'
   */
  size?: "big" | "large" | "medium" | "tiny";
}
```

---

# Dialog 이해하기 (/tds-mobile/components/Dialog/dialog/)

# Dialog 이해하기

이 문서를 읽고나면,

- `Dialog` 컴포넌트의 구조와 `AlertDialog` 컴포넌트와 `ConfirmDialog` 컴포넌트의 차이를 이해할 수 있어요.

[Preview: Basic]

## 이해하기

`Dialog` 컴포넌트는 사용자에게 중요한 정보를 전달하거나 선택을 요구할 때 사용되는 모달 인터페이스에요.
주로 작업 완료 알림, 상태 변경 알림, 또는 사용자의 확인이 필요한 중요한 액션을 수행할 때 사용돼요.

### AlertDialog vs ConfirmDialog

`AlertDialog` 컴포넌트와 `ConfirmDialog` 컴포넌트는 모두 사용자와의 상호작용을 위한 UI를 제공해요. 차이점은 버튼의 개수와 용도에요.

다음은 `AlertDialog`와 `ConfirmDialog`의 차이를 비교한 표에요.

| 타입          | 설명                                                                                                                 | 문서                                                    |
| :------------ | :------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------ |
| AlertDialog   | **단일 버튼**을 통해 **알림을 확인**하는 형태에요.<br/>주로 작업 완료나 상태 변경을 알릴 때 사용해요.                | [AlertDialog 문서](/components/Dialog/alert-dialog)     |
| ConfirmDialog | **두 개의 버튼**을 통해 **사용자의 선택을 받는** 형태에요.<br/>주로 중요한 액션의 실행 전 확인이 필요할 때 사용해요. | [ConfirmDialog 문서](/components/Dialog/confirm-dialog) |

### Dialog의 구성 요소

`Dialog` 컴포넌트는 다음과 같은 구성 요소들로 이루어져 있어요.

1. **제목 (Title)**

   - 주요 메시지를 표시해요.
   - `AlertDialog.Title` 컴포넌트 또는 `ConfirmDialog.Title` 컴포넌트를 사용해요.

2. **설명 (Description)**

   - 부가적인 설명이 필요할 때 사용해요.
   - `AlertDialog.Description` 또는 `ConfirmDialog.Description` 컴포넌트를 사용해요.
   - 선택적으로 사용할 수 있어요.

3. **버튼**
   - `AlertDialog`: 단일 확인 버튼 (`AlertDialog.AlertButton`)
   - `ConfirmDialog`: 취소/확인 버튼 (`ConfirmDialog.CancelButton`, `ConfirmDialog.ConfirmButton`)

> 각 Dialog 타입의 자세한 사용법은 해당 컴포넌트의 문서를 참고하세요.

---

# GridList (/tds-mobile/components/grid-list/)

# GridList

`GridList` 컴포넌트는 그리드 형태로 `GridList.Item` 컴포넌트들을 배치하는 컴포넌트에요. `GridList.Item` 컴포넌트들은 이미지와 텍스트로 구성되고, 모바일 환경에서 `GridList.Item` 컴포넌트 터치 시 확대 효과를 통해 사용자 피드백을 제공해요.

[Preview: Basic]

## 사용 예제

가장 기본적인 사용 방법이에요. 기본적으로 3열 그리드가 적용돼요.

## 열 개수 설정하기

`column` 속성을 통해 그리드의 열 개수를 설정할 수 있어요. 기본적으로 `3`이 적용돼요. `1`, `2`, `3` 중 하나를 선택할 수 있어요.

### 1열 그리드 적용하기

1열 그리드는 `column` 속성이 `1`인 그리드이에요. `GridList.Item` 컴포넌트들의 내용이 길거나, 중요도가 높은 메뉴를 강조하고 싶을 때 사용하면 좋아요.

**Example: Column1Example**

```tsx
<GridList column={1}>

    }
  >
    1열 그리드
  </GridList.Item>

    }
  >
    1열 그리드
  </GridList.Item>
</GridList>
```

### 2열 그리드 적용하기

2열 그리드는 `column` 속성이 `2`인 그리드이에요. `GridList.Item` 컴포넌트들의 크기를 좀 더 크게 보여주고 싶을 때나, 콘텐츠의 가독성을 높이고 싶을 때 사용하면 좋아요.

**Example: Column2Example**

```tsx
<GridList column={2}>

    }
  >
    2열 그리드
  </GridList.Item>

    }
  >
    2열 그리드
  </GridList.Item>

    }
  >
    2열 그리드
  </GridList.Item>
</GridList>
```

### 3열 그리드 적용하기

3열 그리드는 `column` 속성이 `3`인 그리드이에요. 가장 일반적인 형태로, 많은 `GridList.Item` 컴포넌트들을 한 화면에 효율적으로 보여줄 수 있어요. 카테고리나 메뉴 목록처럼 다양한 옵션을 한눈에 보여주고 싶을 때 적합해요.

**Example: Column3Example**

```tsx
<GridList column={3}>

    }
  >
    3열 그리드
  </GridList.Item>

    }
  >
    3열 그리드
  </GridList.Item>

    }
  >
    3열 그리드
  </GridList.Item>

    }
  >
    3열 그리드
  </GridList.Item>

    }
  >
    3열 그리드
  </GridList.Item>
</GridList>
```

## 인터페이스

**Type: GridListProps**

```typescript
export interface GridListProps extends HTMLAttributes<HTMLUListElement> {
  /**
   * 표시될 열의 개수를 정해요.
   *
   * 기본값은 `3`이고, `1`, `2`, `3` 중 하나를 선택할 수 있어요.
   *
   * @default 3
   */
  column?: 1 | 2 | 3;

  /**
   * `GridList` 컴포넌트의 자식 요소예요.
   *
   * 일반적으로 `GridList.Item` 컴포넌트들이 전달돼요.
   */
  children?: ReactNode;
}
```

**Type: GridListItemProps**

```typescript
export interface GridListItemProps extends HTMLAttributes<HTMLLIElement> {
  /**
   * `GridList.Item` 컴포넌트에 표시될 이미지를 지정해요.
   *
   * `img 태그`나 기타 `ReactNode`와 같은 요소를 전달할 수 있어요.
   */
  image: ReactNode;

  /**
   * `GridList.Item` 컴포넌트 하단에 표시될 텍스트에요.
   *
   * `children`으로 전달된 텍스트는 `Paragraph` 컴포넌트를 통해 렌더링돼요.
   */
  children?: ReactNode;
}
```

---

# Highlight (/tds-mobile/components/highlight/)

export function getPreviewBox(PreviewComponent) {
return (
[Preview: VirtualRoot]
);
}

# Highlight

`Highlight` 컴포넌트는 화면의 특정 영역을 강조해서 보여줄 때 사용해요.

{getPreviewBox(Preview)}

## 사용법

### 형태

`Highlight` 컴포넌트는 강조하고 싶은 영역을 `children`으로 감싸는 형태로 사용할 수 있어요. `Highlight` 컴포넌트가 열리면 강조한 영역을 제외한 화면 전체가 어두워져요.

```tsx
<Highlight open>
  <div>하이라이팅될 아이템</div>
</Highlight>
```

#### 강조하고 싶은 영역에 padding 적용하기

`Highlight` 컴포넌트는 강조하고 싶은 영역에 padding을 적용할 수 있어요.

{getPreviewBox()}

```tsx
<Highlight padding={10}>
  <div>하이라이팅될 아이템</div>
</Highlight>
```

### 메시지 표시

`Highlight` 컴포넌트에 강조 영역을 설명할 메시지를 표시할 수 있어요.

{getPreviewBox()}

```tsx
<Highlight message="하이라이트 메시지" messageXAlignment="center">
  <div>하이라이팅될 아이템</div>
</Highlight>
```

#### 메시지 정렬과 색상 조정하기

메시지의 가로/세로 정렬 방식과 색상을 조정할 수 있어요. 이때, 세로 정렬을 변경하면 화살표 아이콘의 위치가 세로 정렬 값에 따라 따라 달라지지만, 가로 정렬을 변경해도 화살표 아이콘의 위치는 항상 중앙으로 고정돼요.

정렬 값을 설정하지 않으면 화면 너비와 강조 영역의 너비를 비교해서 결정해요.

{getPreviewBox(

)}

```tsx
<Highlight
  message="하이라이트 메시지가 많이 긴 경우, 정렬 방식을 변경해서 표시할 수 있어요."
  messageXAlignment="right"
  messageYAlignment="bottom"
  messageColor="pink"
>
  <div>하이라이팅될 아이템</div>
</Highlight>
```

### 앱브릿지와 함께 사용하기

토스 앱 환경 내에서 앱브릿지로 네이티브 `Highlight` 컴포넌트를 호출할 수 있어요. 앱 내 특정 화면이나 단계에서 사용자의 주목을 유도하는 데 유용해요. 자세한 내용은 앱브릿지 문서(`showHighlight`)를 참고해주세요.

## 인터페이스

**Type: HighlightProps**

```typescript
export interface HighlightProps {
  /**
   * 강조 영역을 표시할지 여부예요.
   * `true`로 설정하면 강조된 영역을 보여주고, `false`로 설정하면 강조가 해제돼요.
   */
  open: boolean;
  /**
   * 강조할 영역 내부의 패딩 크기를 설정해요. 단위는 `px`이에요.
   * 예를 들어, `padding={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   * @default 0
   */
  padding?: number;
  /**
   * 강조할 영역이 표시되기 전 지연 시간을 설정해요. 초 단위를 사용해요.
   * 예를 들어, `delay={2}`로 설정하면 2초 후에 강조 영역이 나타나요.
   *
   * @default 0
   *
   */
  delay?: number;
  /**
   * 강조할 영역 외부에 추가 스타일링을 위해 `className`을 설정해요.
   */
  highlighterClassname?: string;
  /**
   * 강조할 영역 외부에 표시할 설명 메시지에요.
   * 문자열을 직접 전달하거나, `color`와 `style` 속성을 갖는 함수를 전달할 수 있어요.
   * 예를 들어, 함수를 사용해 동적 메시지 스타일링이 가능해요.
   */
  message?:
    | string
    | ((props: { color?: string; style: CSSProperties }) => ReactElement);
  /**
   * 강조할 메시지의 색상이에요. 색상 코드를 문자열로 지정해요.
   * 기본값은 `colors.white`예요.
   * @default colors.white
   */
  messageColor?: string;
  /**
   * 강조할 메시지의 가로 정렬 방식이에요. 기본값은 화면 너비와 강조 영역의 너비를 비교해서 자동으로 결정돼요.
   */
  messageXAlignment?: "left" | "center" | "right";
  /**
   * 강조할 메시지의 세로 정렬 방식이에요. 기본값은 화면 높이와 강조 영역의 높이를 비교해서 자동으로 결정돼요.
   */
  messageYAlignment?: "top" | "bottom";
  /**
   * 강조할 영역 외부를 클릭했을 때 실행되는 함수예요.
   */
  onClick?: () => void;
  /**
   * 강조 애니메이션이 종료되었을 때 실행되는 함수예요.
   * 애니메이션이 끝난 후 실행할 추가 작업이 있을 때 사용할 수 있어요.
   */
  onExited?: () => void;
}
```

---

# Icon Button (/tds-mobile/components/icon-button/)

# Icon Button

`IconButton` 컴포넌트는 사용자가 특정 작업을 실행하거나 이벤트를 트리거할 때 사용해요. 아이콘으로 기능을 직관적으로 전달하면서, UI를 간결하게 유지할 수 있어요.

[Preview: Basic]

## 사용법

### 형태

`IconButton`의 형태를 변경하려면 `variant` 속성을 사용하세요. 선택할 수 있는 값은 `'clear'`, `'fill'`, `'border'`가 있어요.

#### clear

배경 없이 아이콘만 보여주고 싶다면 `variant` 속성에 `'clear'`를 넣어주세요. 클릭한 상태에서는 배경 색이 보여요.

**Example: Clear**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

#### fill

아이콘 버튼에 배경색을 추가하려면 `variant`에 `'fill'`을 넣어주세요. 배경이 채워진 스타일로 아이콘이 강조돼요. 클릭한 상태에서는 배경 색이 사라져요.

**Example: Fill**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

#### border

테두리가 있는 스타일을 원한다면 `variant` 속성에 `'border'`를 넣어주세요. 버튼에 테두리가 생겨 아이콘이 구분되어 보여요. 클릭한 상태에서는 배경 색이 보여요.

**Example: Border**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

### 아이콘 색 변경하기

아이콘 색을 변경하려면 `color` 속성을 사용하세요. 아이콘의 이름이 `-mono`로 끝나는 모노타입의 아이콘만 색을 변경할 수 있어요.

**Example: Colors**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

### 배경 색 변경하기

`IconButton` 컴포넌트의 배경 색을 변경하려면 `bgColor` 속성을 사용하세요. `variant` 속성의 값이 `'fill'`일 때는 지정한 색이 배경 색으로 적용되고, `'clear'`나 `'border'`일 때는 버튼을 눌렀을 때 배경 색으로 적용돼요.

**Example: BgColors**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

### 크기 조정하기

아이콘의 크기를 변경하려면 `iconSize` 속성을 사용하세요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: "8px" }}></div>
```

## 접근성

`IconButton` 컴포넌트에는 `aria-label` 속성을 필수 값으로 지정해야해요. 아이콘만으로는 어떤 역할인지 알 수 없기 때문이에요.  
클릭을 통해 동작하는 액션을 `aria-label`을 통해 명시적으로 작성해주세요.

```tsx
<IconButton
  src="https://static.toss.im/icons/svg/icon-search-bold-mono.svg"
  aria-label="검색하기"
/>
```

## 인터페이스

**Type: IconButtonProps**

```typescript
export interface IconButtonProps {
  /**
   * `IconButton` 컴포넌트의 형태를 결정해요.
   *
   * @default 'clear'
   */
  variant?: "fill" | "clear" | "border";
  /**
   * 사용할 아이콘의 URL을 지정해요. `src` 속성은 `name` 속성과 함께 사용할 수 없고, 아이콘이나 2D Emoji 리소스의 URL만 지정할 수 있어요.
   */
  src?: string;
  /**
   * 사용할 아이콘의 이름을 지정해요. `name` 속성은 `src` 속성과 함께 사용할 수 없고, 아이콘이나 2D Emoji 리소스의 이름만 지정할 수 있어요.
   */
  name?: string;
  /**
   * 사용할 아이콘의 색상을 지정해요. 아이콘의 이름이 `-mono`로 끝나는 모노타입 아이콘을 사용할 때만 색상을 지정할 수 있어요.
   */
  color?: string;
  /**
   * `IconButton` 컴포넌트의 배경색을 지정해요.
   *
   * @default adaptive.greyOpacity100
   */
  bgColor?: string;
  /**
   * 이 값에 맞춰 아이콘의 크기를 변경해요. 예를 들어 이 값이 `24`라면, '24px'이 크기로 적용돼요.
   *
   * @default 24
   */
  iconSize?: number;
  /**
   * IconButton에서 aria-label은 필수 값입니다.
   * 아이콘만으로는 어떤 역할인지 알 수 없기 때문입니다.
   */
  "aria-label": string;
}
```

---

# Alphabet Keypad (/tds-mobile/components/Keypad/alphabet-keypad/)

# Alphabet Keypad

`AlphabetKeypad` 컴포넌트는 알파벳이 표시된 키패드로, 주로 알파벳을 입력하는 인증 번호나 코드를 입력할 때 사용해요. 키를 자유롭게 배치할 수 있어서, 원하는 입력 방식에 맞는 키패드를 구성할 수 있어요.

[Preview: Basic]

## 사용법

### 키 배치 커스텀하기

`alphabets` 속성을 사용하면 키패드에 표시될 알파벳을 자유롭게 정하고 배치할 수 있어요. 이 속성에 원하는 알파벳을 배열로 전달하면, 해당 값들이 설정한 순서대로 키패드에 표시돼요.

**Example: Customs**

```tsx
<AlphabetKeypad
  alphabets={[
    "z",
    "y",
    "x",
    "w",
    "v",
    "u",
    "t",
    "s",
    "r",
    "q",
    "p",
    "o",
    "n",
    "m",
    "l",
    "k",
    "j",
    "i",
    "h",
    "g",
    "f",
    "e",
    "d",
    "c",
    "b",
    "a",
  ]}
  onKeyClick={() => {}}
  onBackspaceClick={() => {}}
/>
```

## 인터페이스

**Type: AlphabetKeypadProps**

```typescript
export interface AlphabetKeypadProps {
  /**
   * `AlphabetKeypad` 컴포넌트에 표시할 알파벳 배열이에요. 대소문자를 구분할 수 있으며, 배열에 포함된 순서대로 버튼이 만들어져요. 배열을 전달하지 않으면 기본적으로 대문자 A-Z가 표시돼요.
   *
   * @default ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
   */
  alphabets?: (
    | "A"
    | "a"
    | "B"
    | "b"
    | "C"
    | "c"
    | "D"
    | "d"
    | "E"
    | "e"
    | "F"
    | "f"
    | "G"
    | "g"
    | "H"
    | "h"
    | "I"
    | "i"
    | "J"
    | "j"
    | "K"
    | "k"
    | "L"
    | "l"
    | "M"
    | "m"
    | "N"
    | "n"
    | "O"
    | "o"
    | "P"
    | "p"
    | "Q"
    | "q"
    | "R"
    | "r"
    | "S"
    | "s"
    | "T"
    | "t"
    | "U"
    | "u"
    | "V"
    | "v"
    | "W"
    | "w"
    | "X"
    | "x"
    | "Y"
    | "y"
    | "Z"
    | "z"
  )[];
  /**
   * `AlphabetKeypad` 컴포넌트에서 알파벳 키를 클릭했을 때 실행되는 함수예요. 클릭된 알파벳 값이 `value`로 전달돼요.
   */
  onKeyClick: (value: string) => void;
  /**
   * `AlphabetKeypad` 컴포넌트에서 `backspace` 키를 클릭하면 실행되는 함수예요. 기본적으로 마지막 입력 값을 삭제하는 데 사용되지만, 이 함수에 원하는 동작을 추가해 다양한 상황에 맞게 활용할 수 있어요. 예를 들어, 삭제 전에 확인 메시지를 표시하는 동작을 구현할 수 있어요.
   */
  onBackspaceClick: () => void;
}
```

---

# Full Secure Keypad (/tds-mobile/components/Keypad/full-secure-keypad/)

# Full Secure Keypad

`FullSecureKeypad` 컴포넌트는 숫자와 알파벳을 함께 표시하는 보안 키패드예요. 숫자와 문자를 모두 입력할 수 있으며, 비밀번호나 인증번호 입력처럼 보안이 중요할 때 사용해요. 키패드의 각 키 사이에 랜덤으로 공백이 배치되어 있어, 입력 패턴을 쉽게 추측할 수 없도록 설계되었어요. 사용자가 입력을 마치면 제출할 수 있는 버튼도 함께 제공해요.

[Preview: Basic]

## 사용법

### 키패드 공백 위치 무작위로 바꾸기

`FullSecureKeypad`의 공백 위치를 무작위로 변경하려면 `FullSecureKeypadRef` 타입의 `ref`를 전달하세요. `ref.current.reorderEmptyCells` 함수를 호출하면 키패드의 공백 위치를 무작위로 바꿀 수 있어요.

**Example: RandomBlanks**

```tsx
function RandomBlanks() {
  const [_, setState] = React.useState(false);
  const ref = React.useRef({
    reorderEmptyCells: () => {},
    element: null,
  });

  return (
    <FullSecureKeypad
      ref={ref}
      onKeyClick={() => {}}
      onBackspaceClick={() => {}}
      onSpaceClick={() => {}}
      onSubmit={() => {
        if (ref.current) {
          ref.current.reorderEmptyCells();
          setState((prev) => !prev); // 의도적으로 리렌더링을 트리거합니다.
        }
      }}
      submitButtonText="공백 옮기기"
    />
  );
}
```

## 인터페이스

**Type: FullSecureKeypadProps**

```typescript
export interface FullSecureKeypadProps {
  /**
   * `FullSecureKeypad` 컴포넌트의 숫자 또는 알파벳 키를 클릭하면 실행되는 함수예요.
   */
  onKeyClick: (value: string) => void;
  /**
   * `FullSecureKeypad` 컴포넌트에서 `backspace` 키를 클릭하면 실행되는 함수예요. 기본적으로 마지막 입력 값을 삭제하는 데 사용되지만, 이 함수에 원하는 동작을 추가해 다양한 상황에 맞게 활용할 수 있어요. 예를 들어, 삭제 전에 확인 메시지를 표시하는 동작을 구현할 수 있어요.
   */
  onBackspaceClick: () => void;
  /**
   * `FullSecureKeypad` 컴포넌트의 `space` 키를 클릭하면 실행되는 함수예요.
   */
  onSpaceClick: () => void;
  /**
   * `FullSecureKeypad` 컴포넌트의 입력 완료 키를 클릭하면 실행되는 함수예요.
   */
  onSubmit: () => void;
  /**
   * 이 값이 `true`일 때 입력 완료 키가 비활성화돼요.
   *
   * @default false
   */
  submitDisabled?: boolean;
  /**
   * 입력을 완료한 후 제출할 때 클릭하는 키 버튼에 표시할 텍스트예요.
   *
   * @default '입력 완료'
   */
  submitButtonText?: string;
}
```

**Type: FullSecureKeypadRef**

```typescript
export interface FullSecureKeypadRef {
  /**
   * 키패드의 공백 위치를 무작위로 재배치하는 함수예요. 보안을 강화하기 위해 사용해요.
   */
  reorderEmptyCells: () => void;
  /**
   * `FullSecureKeypad` 컴포넌트의 DOM 요소에 대한 참조예요. DOM에 ref를 할당해야 할 때 사용해요.
   */
  element: HTMLDivElement | null;
}
```

---

# Number Keypad (/tds-mobile/components/Keypad/number-keypad/)

# Number Keypad

`NumberKeypad` 컴포넌트는 숫자가 표시된 키패드로, 주로 숫자로 된 비밀번호를 입력할 때 사용해요. 키를 자유롭게 배치할 수 있어서, 원하는 입력 방식에 맞는 키패드를 구성할 수 있어요.

[Preview: Basic]

## 사용법

### 키 배치 커스텀하기

`numbers` 속성을 사용해서 키패드에 표시할 숫자를 자유롭게 정하고 배치할 수 있어요. 이 속성에 원하는 숫자를 배열로 전달하면, 해당 값들이 설정한 순서대로 키패드에 표시돼요.

**Example: Customs**

```tsx
<NumberKeypad
  numbers={[1, 3, 5, 7, 9, 2, 4, 6, 8, 0]}
  onKeyClick={() => {}}
  onBackspaceClick={() => {}}
/>
```

### 보안 키패드로 활용하기

보안이 필요한 입력값이 있을 때는 `secure` 속성을 사용하세요. 이 기능은 사용자가 클릭한 숫자와 함께, 상하좌우에 있는 숫자를 제외한 무작위 두 개의 숫자가 함께 눌린 것처럼 처리해요. 즉, 사용자가 어떤 숫자를 입력했는지 알아보기 어려워 보안이 강화돼요.

또, 앱이 백그라운드로 이동될 때 앱의 화면을 가리고 Android 기기에서는 스크린 캡쳐를 막아줘요.

**Example: Secures**

```tsx
<NumberKeypad secure={true} onKeyClick={() => {}} onBackspaceClick={() => {}} />
```

> 사용자의 주민등록번호 뒷자리를 입력받을 때는 보안을 위해 `secure` 속성을 반드시 `true`로 설정해주세요.

## 인터페이스

**Type: NumberKeypadProps**

```typescript
export interface NumberKeypadProps {
  /**
   * `NumberKeypad` 컴포넌트에 표시할 숫자들의 배열이에요. 배열에 포함된 순서대로 버튼이 만들어져요.
   *
   * @default [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
   */
  numbers?: (0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9)[];
  /**
   * 이 값이 `true`라면 보안 키패드로 동작해요. 클릭한 숫자 키의 상하좌우에 있는 키를 제외한 무작위의 숫자 키 2개가 눌린 것처럼 처리돼요.
   *
   * @default false
   */
  secure?: boolean;
  /**
   * `NumberKeypad` 컴포넌트의 숫자 키를 클릭하면 실행되는 함수예요.
   */
  onKeyClick: (value: string) => void;
  /**
   * `NumberKeypad` 컴포넌트에서 `backspace` 키를 클릭하면 실행되는 함수예요. 기본적으로 마지막 입력 값을 삭제하는 데 사용되지만, 이 함수에 원하는 동작을 추가해 다양한 상황에 맞게 활용할 수 있어요. 예를 들어, 삭제 전에 확인 메시지를 표시하는 동작을 구현할 수 있어요.
   */
  onBackspaceClick: () => void;
}
```

---

# ListFooter (/tds-mobile/components/list-footer/)

# ListFooter

`ListFooter` 컴포넌트는 리스트 항목의 마지막 부분에 위치해, 사용자에게 더 많은 항목을 불러오거나 목록을 확장하는 기능을 제공해요.
기본적으로 "더 보기"와 같은 텍스트를 표시해 리스트가 이어질 수 있다는 암시를 주고, 다양한 옵션으로 시각적 요소를 맞춤 설정할 수 있어요.

[Preview: Basic]

## 사용법

### 텍스트 사용하기

리스트의 마지막에 "더 보기" 같은 텍스트를 표시하고 싶다면 `children`에 문자열을 전달하세요.
문자열을 전달하면 `ListFooter.Text` 컴포넌트를 사용해 텍스트가 렌더링돼요. 컴포넌트를 전달하면 그대로 렌더링돼요.

**Example: Text**

```tsx
<div>
  <ListFooter>더 보기</ListFooter>
  <ListFooter textColor={adaptive.grey600}>더 보기</ListFooter>
  <ListFooter>
    <ListFooter.Text color={adaptive.blue400} fontWeight="bold">
      더 보기
    </ListFooter.Text>
  </ListFooter>
</div>
```

### 아이콘과 함께 사용하기

"더 보기" 기능을 아이콘으로 표현하려면 `icon` 속성을 활용하세요.
문자열을 전달하면 `ListFooter.Icon` 컴포넌트와 함께 해당 아이콘이 렌더링돼요. 아이콘 컴포넌트를 직접 전달하면 그대로 렌더링돼요.

**Example: WithIcon**

```tsx
<div>
  <ListFooter icon="icon-plus-small-mono">더 보기</ListFooter>
  <ListFooter icon="icon-arrow-down-mono" iconColor={adaptive.grey600} textColor={adaptive.grey600}>
    더 보기
  </ListFooter>
  }
  >
    더 보기
  </ListFooter>
</div>
```

### 상단 구분선 조정하기

`border` 속성을 사용해 `ListFooter`의 상단 구분선 스타일을 조정할 수 있어요. `border` 값에 따라 리스트의 시작 부분을 강조하거나 깔끔하게 보여줄 수 있어요.

- `full`: 리스트의 시작에 가느다란 구분선을 전체 너비로 표시해요. 기본값으로 설정된 옵션이며, `ListFooter`의 경계를 분명히 하고 싶을 때 적합해요.
- `indented`: 좌측 여백을 두고 구분선을 표시헤요. 리스트 내용과 자연스럽게 연결하고 싶을 때 사용해요.
- `none`: 구분선을 표시하지 않아요. 구분이 필요없거나 리스트가 하나로 이어진 느낌을 줄 때 사용해요.

또한 `hairline` 속성을 사용해 `ListFooter`의 구분선을 더 세밀하게 설정할 수 있어요. <br/>
`hairline`은 `ListFooter.Hairline` 컴포넌트를 렌더링 할 수 있고, `indent` 속성을 설정해 구분선의 왼쪽 여백을 픽셀 단위로 설정할 수 있어요.
예를 들어, `indent={50}`을 사용하면 구분선이 50px의 여백을 두고 렌더링돼요.

**Example: Border**

```tsx
<div>
  <ListFooter border="full">더 보기</ListFooter>
  <ListFooter border="indented">더 보기</ListFooter>
  <ListFooter border="none">더 보기</ListFooter>
  }>
    더 보기
  </ListFooter>
</div>
```

### 그림자 효과 주기

`ListFooter`에 `onClick` 속성을 추가하면 클릭 시 그림자 효과가 나타나요. 이 효과는 사용자가 `ListFooter`와 상호작용하고 있음을 시각적으로 나타내며, 리스트가 확장되거나 더 많은 항목을 불러오는 동작임을 암시할 수 있어요.

또한 `shadow` 속성을 사용해 `ListFooter`의 그림자 효과를 더 세밀하게 설정할 수 있어요. <br/>
`ListFooter.Shadow` 컴포넌트와 `style` 속성을 조합하면 원하는 그림자 스타일을 적용할 수 있어요.

**Example: Shadow**

```tsx
function Shadow() {
  const onClick = () => {};
  return (
    <div>
      <ListFooter icon="icon-plus-small-mono" onClick={onClick}>
        더 보기
      </ListFooter>

        }
      >
        더 보기
      </ListFooter>
    </div>
  );
}
```

## 접근성

### 개발자가 추가로 지원해야 하는 접근성

#### 필수로 제공해야 하는 aria-label

`ListFooter` 컴포넌트에서는 `aria-label` 속성을 필수적으로 제공해서 `ListFooter` 버튼의 목적을 명확히 설명해야 합니다.  
스크린 리더 사용자는 무엇에 대한 버튼인지 조금 더 구체적인 설명이 필요합니다. 화면을 보는 경우 위 아래 맥락을 파악하여 더보기에 대한 용도가 쉽게 파악이 되지만, 스크린 리더 사용자는 화면의 맥락을 파악한 상태에서 버튼에 접근하지 못할 가능성도 있기 때문입니다.

```jsx
<ListFooter
  onClick={goToNextPage}
  aria-label="다음 페이지로 이동하기" // 개발자가 필수로 제공해야 합니다
>
  <ListFooter.Text>더 보기</ListFooter.Text>
</ListFooter>
```

## 인터페이스

**Type: ListFooterProps**

```typescript
export interface ListFooterProps {
  /**
   * 상단 구분선의 스타일을 설정해요.
   * - `full`: 전체 너비로 표시해요.
   * - `indented`: 좌측 여백을 두고 구분선을 표시해요.
   * - `none`: 구분선을 표시하지 않아요.
   * @default full
   */
  border?: "full" | "indented" | "none";
  /**
   * 아이콘을 설정해요.
   * 문자열을 입력하면 `ListFooter.Icon` 컴포넌트와 함께 렌더링하고, `ReactElement`를 입력하면 전달한 컴포넌트를 그대로 렌더링해요.
   */
  icon?: "ReactElement" | "string";
  /**
   * 상단 구분선을 설정해요.
   * 색상이나 간격 등을 수정하고 싶을 때 사용해요.
   * `ListFooter.Hairline` 컴포넌트 또는 다른 선 컴포넌트를 사용해서 스타일을 커스터마이징할 수 있어요.
   */
  hairline?: ReactElement;
  /**
   * `onClick` 속성이 있을 때 보이는 속성이에요. 기본 스타일을 변경하고 싶을 때 사용해요.
   * `ListFooter.Shadow` 컴포넌트 또는 다른 선 컴포넌트를 사용해서 스타일을 커스터마이징할 수 있어요.
   */
  shadow?: ReactElement;
  /**
   * 텍스트 색상을 설정해요.
   * @default adaptive.blue500
   */
  textColor?: string;
  /**
   * 아이콘 색상을 설정해요.
   * @default adaptive.blue500
   */
  iconColor?: string;
  /**
   * "더 보기"와 같은 하위 텍스트를 설정해요.
   * 전달된 값이 문자열이라면 `ListFooter.Text` 컴포넌트와 함께 렌더링하고, ReactElement 라면 전달한 컴포넌트를 그대로 렌더링해요.
   */
  children?: "string" | "ReactElement";
}
```

**Type: ListFooterTextProps**

```typescript
export interface ListFooterTextProps {
  /**
   * 텍스트의 색상을 설정해요.
   */
  color?: string;
  /**
   * 텍스트의 두께 스타일을 설정해요.
   * @default medium
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: ListFooterIconProps**

```typescript
export interface ListFooterIconProps {
  /**
   * 아이콘의 색상을 설정해요.
   */
  color?: string;
  /**
   * 사용할 아이콘의 이름을 지정해요.
   */
  name: string;
}
```

**Type: ListFooterHairLineProps**

```typescript
export interface ListFooterHairLineProps {
  /**
   * 좌측 여백을 설정해요.
   * 단위는 `px`이에요. 예를 들어, `indent={10}`으로 설정하면 좌측에 10px의 여백이 생겨요.
   */
  indent?: number;
}
```

---

# ListHeader (/tds-mobile/components/list-header/)

# ListHeader

[Image: ListHeader thumbnail - list-header/Thumbnail-ListHeader.png]

`ListHeader` 컴포넌트는 사용자가 특정 동작을 실행하거나 추가 정보로 안내될 수 있는 헤더 UI 요소예요. 페이지나 섹션의 상단에 배치되어 사용자에게 제목, 설명, 그리고 상호작용 가능한 요소를 제공할 수 있어요. 주로 제목, 오른쪽의 부가 콘텐츠, 보조 설명을 포함해요.

[Preview: Basic]

## 사용 예제

### 위치

`ListHeader` 컴포넌트의 보조 설명은 `descriptionPosition` 속성을 통해
위 또는 아래에 배치될 수 있어요. `top`과 `bottom` 두 가지를 제공해요.
기본적으로 `descriptionPosition`은 `top`으로 설정되어 있지만,
`bottom` 값을 주면 설명이 제목 아래에 배치돼요.

**Example: BasicHeaders**

```tsx
<div style={{ display: "flex", gap: "32px", flexDirection: "column" }}>
  <ListHeader
    title={
      <ListHeader.TitleParagraph
        typography="t5"
        color={adaptive.grey800}
        fontWeight="bold"
      >
        타이틀 내용
      </ListHeader.TitleParagraph>
    }
    right={
      <ListHeader.RightText typography="t7" color={adaptive.grey700}>
        악세사리
      </ListHeader.RightText>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
  />

  <ListHeader
    title={
      <ListHeader.TitleParagraph
        typography="t5"
        color={adaptive.grey800}
        fontWeight="bold"
      >
        타이틀 내용
      </ListHeader.TitleParagraph>
    }
    right={
      <ListHeader.RightText typography="t7" color={adaptive.grey700}>
        악세사리
      </ListHeader.RightText>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
    descriptionPosition="bottom"
  />
</div>
```

### 제목

`ListHeader`에서 제목을 사용하는 방법으로 `ListHeader.TitleParagraph`,
`ListHeader.TitleTextButton`, `ListHeader.TitleSelector` 세 가지 방법을 제공하고 있어요.

#### 제목으로 텍스트(문단) 사용하기

`ListHeader` 컴포넌트에서 제목을 텍스트(문단)로 설정할 때,
`title` 속성에 `ListHeader.TitleParagraph`을 사용해요.
`ListHeader.TitleParagraph`은 `typography`와 `fontWeight`를 지정해 스타일을 변경할 수 있어요.

**Example: Basic**

```tsx
<ListHeader
  title={
    <ListHeader.TitleParagraph
      typography="t5"
      color={adaptive.grey800}
      fontWeight="bold"
    >
      타이틀 내용
    </ListHeader.TitleParagraph>
  }
  right={
    <ListHeader.RightText typography="t7" color={adaptive.grey700}>
      악세사리
    </ListHeader.RightText>
  }
  description={
    <ListHeader.DescriptionParagraph>
      보조설명 내용
    </ListHeader.DescriptionParagraph>
  }
  rightAlignment="center"
/>
```

#### 제목으로 텍스트 버튼 사용하기

`ListHeader` 컴포넌트에서 제목을 클릭할 수 있는 텍스트 버튼으로 설정할 때,
`title` 속성에 `ListHeader.TitleTextButton`을 사용해요.
`ListHeader.TitleTextButton`은 `size` 속성을 지정해 크기를 변경할 수 있어요.

형태는 `variant` 속성으로 `TextButton` 컴포넌트의 타입으로 정의된 `clear`, `arrow`, `underline` 세 가지를 제공해요.

**Example: TextButtonVariantsHeaders**

```tsx
<div style={{ display: "flex", gap: "32px", flexDirection: "column" }}>
  <ListHeader
    title={
      <ListHeader.TitleTextButton
        size="large"
        color={adaptive.grey600}
        fontWeight="bold"
        variant="arrow"
      >
        타이틀 내용
      </ListHeader.TitleTextButton>
    }
    right={
      <ListHeader.RightText typography="t6" color={adaptive.grey700}>
        악세사리
      </ListHeader.RightText>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
  />
  <ListHeader
    title={
      <ListHeader.TitleTextButton
        size="large"
        color={adaptive.grey600}
        fontWeight="bold"
        variant="arrow"
      >
        타이틀 내용
      </ListHeader.TitleTextButton>
    }
    right={
      <ListHeader.RightText typography="t6" color={adaptive.grey700}>
        악세사리
      </ListHeader.RightText>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
  />
  <ListHeader
    title={
      <ListHeader.TitleTextButton
        size="large"
        color={adaptive.grey600}
        fontWeight="bold"
        variant="underline"
      >
        타이틀 내용
      </ListHeader.TitleTextButton>
    }
    right={
      <ListHeader.RightText typography="t6" color={adaptive.grey700}>
        악세사리
      </ListHeader.RightText>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
  />
</div>
```

#### 제목으로 셀렉터 사용하기

제목에 선택 가능한 드롭다운 스타일의 셀렉터를 사용하고 싶을 때, `title` 속성에
`ListHeader.TitleSelector`를 사용해요. `ListHeader.TitleSelector`은
`typography`를 지정해 스타일을 변경할 수 있어요.

**Example: SelectorHeader**

```tsx
<ListHeader
  title={
    <ListHeader.TitleSelector
      typography="t4"
      color={adaptive.grey800}
      fontWeight="bold"
    >
      타이틀 내용
    </ListHeader.TitleSelector>
  }
  right={
    <ListHeader.RightText typography="t6" color={adaptive.grey700}>
      악세사리
    </ListHeader.RightText>
  }
  description={
    <ListHeader.DescriptionParagraph>
      보조설명 내용
    </ListHeader.DescriptionParagraph>
  }
  rightAlignment="center"
/>
```

### 화살표

오른쪽에 화살표 아이콘과 텍스트를 배치하려면 `ListHeader.RightArrow`를 사용해요.
`ListHeader.RightArrow`는 클릭 가능한 요소로 사용할 수 있고,
`onClick`을 추가해 클릭 시 발생하는 동작을 정의할 수 있어요.

**Example: HeadersWithArrow**

```tsx
<div style={{ display: "flex", gap: "32px", flexDirection: "column" }}>
  <ListHeader
    title={
      <ListHeader.TitleParagraph
        typography="t7"
        color={adaptive.grey800}
        fontWeight="bold"
      >
        타이틀 내용
      </ListHeader.TitleParagraph>
    }
    right={
      <ListHeader.RightArrow typography="t6">악세사리</ListHeader.RightArrow>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
  />

  <ListHeader
    title={
      <ListHeader.TitleParagraph
        typography="t7"
        color={adaptive.grey800}
        fontWeight="bold"
      >
        타이틀 내용
      </ListHeader.TitleParagraph>
    }
    right={
      <ListHeader.RightArrow typography="t6">악세사리</ListHeader.RightArrow>
    }
    description={
      <ListHeader.DescriptionParagraph>
        보조설명 내용
      </ListHeader.DescriptionParagraph>
    }
    rightAlignment="center"
    descriptionPosition="bottom"
  />
</div>
```

## 인터페이스

**Type: ListHeaderProps**

```typescript
export interface ListHeaderProps {
  /**
   * ListHeader에 표시될 제목 요소예요.
   *
   * 제목 요소로 `ListHeader.TitleParagraph`, `ListHeader.TitleSelector`, `ListHeader.TitleTextButton`을 사용해주세요.
   */
  title: ReactNode;

  /**
   * 제목이 차지하는 너비의 비율을 정의해요.
   *
   * `right` 속성이 설정되어 있다면, 제목과 `right`의 비율을 설정해요. 제목의 비율이 200% 이하일 때는 `titleWidthRatio`에 따라 결정되고, 200% 이상일 때는 `0.5`로 고정돼요.
   *
   * 더 큰 텍스트 비율이 200% 이상이면 `0.5`로 고정돼요.
   *
   * @default 0.66
   */
  titleWidthRatio?: number;

  /**
   * `ListHeader`에 표시될 설명 요소예요.
   *
   * `ListHeader.DescriptionParagraph`를 사용해 주세요.
   *
   * @default undefined
   */
  description?: ReactNode;

  /**
   * 설명 텍스트의 위치를 지정해요.
   *
   * `top`, `bottom` 두 가지 옵션을 제공하고 있어요.
   *
   * - `top`: 설명이 제목 위에 배치돼요. (기본값)
   * - `bottom`: 설명이 제목 아래에 배치돼요.
   *
   * @default 'top'
   */
  descriptionPosition?: "top" | "bottom";

  /**
   * ListHeader의 오른쪽에 표시될 요소예요.
   *
   * 오른쪽 요소는 `ListHeader.RightText` 또는 `ListHeader.RightArrow`로 정의할 수 있어요.
   *
   * @default undefined
   */
  right?: ReactNode;

  /**
   * 오른쪽 요소의 정렬을 정의해요.
   *
   * @default 'center'
   */
  rightAlignment?: "center" | "bottom";
}
```

**Type: ListHeaderDescriptionParagraphProps**

```typescript
export interface ListHeaderDescriptionParagraphProps {
  /**
   * 설명 문단으로 표시될 자식 요소예요.
   *
   * ListHeader의 설명 섹션에 사용돼요.
   */
  children: ReactNode;
}
```

**Type: ListHeaderRightArrowProps**

```typescript
export interface ListHeaderRightArrowProps {
  /**
   * 화살표 옆에 표시될 텍스트의 타이포그래피 스타일을 설정해요.
   *
   * 't7' 또는 't6' 타이포그래피 스타일 중 하나를 사용할 수 있어요.
   */
  typography: "t7" | "t6";

  /**
   * 화살표 옆에 표시될 요소예요.
   *
   * 텍스트나 다른 요소를 넣을 수 있어요.
   */
  children?: ReactNode;

  /**
   * 화살표 아이콘의 색상이에요.
   *
   * @default adaptive.grey400
   */
  color?: string;

  /**
   * 화살표 옆에 표시되는 텍스트의 색상이에요.
   *
   * @default adaptive.grey700
   */
  textColor?: string;

  /**
   * 화살표를 클릭했을 때 호출되는 함수예요.
   *
   * 사용자가 클릭 시 실행할 동작을 정의할 수 있어요.
   *
   * @default undefined
   */
  onClick?: () => void;
}
```

**Type: ListHeaderRightTextProps**

```typescript
export interface ListHeaderRightTextProps {
  /**
   * 오른쪽 텍스트의 타이포그래피 스타일을 설정해요.
   *
   * 't7' 또는 't6' 타이포그래피 스타일 중 하나를 사용할 수 있어요.
   */
  typography: "t7" | "t6";

  /**
   * 오른쪽에 표시될 텍스트 자식 요소예요.
   *
   * 텍스트나 다른 요소를 넣을 수 있어요.
   */
  children: ReactNode;

  /**
   * 텍스트의 색상이에요.
   *
   * @default adaptive.grey700
   */
  color?: string;
}
```

**Type: ListHeaderTitleParagraphProps**

```typescript
export interface ListHeaderTitleParagraphProps {
  /**
   * 제목 텍스트의 글꼴 두께를 설정해요.
   *
   * 'bold', 'medium', 'regular' 중 하나를 선택할 수 있어요.
   */
  fontWeight: "bold" | "medium" | "regular";

  /**
   * 제목으로 표시될 텍스트 자식 요소예요.
   *
   * 텍스트나 다른 요소를 넣을 수 있어요.
   */
  children: ReactNode;

  /**
   * 제목 텍스트의 색상이에요.
   *
   * @default adaptive.grey800
   */
  color?: string;

  /**
   * 제목 텍스트의 타이포그래피 스타일을 설정해요.
   *
   * 't7', 't5', 't4' 중 하나를 선택할 수 있어요.
   */
  typography: "t7" | "t5" | "t4";
}
```

**Type: ListHeaderTitleSelectorProps**

```typescript
export interface ListHeaderTitleSelectorProps {
  /**
   * 제목 텍스트의 타이포그래피 스타일을 설정해요.
   *
   * 't7', 't5', 't4' 중 하나를 선택할 수 있어요.
   */
  typography: "t7" | "t5" | "t4";

  /**
   * 제목 선택자에 표시될 자식 요소예요.
   *
   * 텍스트나 다른 요소를 넣을 수 있어요.
   */
  children: ReactNode;
}
```

**Type: ListHeaderTitleTextButtonProps**

```typescript
export interface ListHeaderTitleTextButtonProps extends TextButtonProps {
  /**
   * 제목 텍스트의 크기를 설정해요.
   *
   * 'xsmall', 'medium', 'large' 중 하나를 선택할 수 있어요.
   */
  size: "xsmall" | "medium" | "large";

  /**
   * 제목 텍스트의 글꼴 두께를 설정해요.
   *
   * 'bold', 'medium', 'regular' 중 하나를 선택할 수 있어요.
   */
  fontWeight: "bold" | "medium" | "regular";

  /**
   * 버튼의 자식 요소로 표시될 요소예요.
   *
   * 텍스트나 다른 요소를 넣을 수 있어요.
   */
  children: ReactNode;

  /**
   * 버튼에 HTML의 `type` 속성을 컴포넌트의 루트 요소로 전달하기 위한 속성이에요.
   *
   * 해당 속성은 현재 임시로 제공되며, 추후 제거될 예정이에요.
   *
   * @default undefined
   */
  htmlType?: string;

  /**
   * 버튼의 형태를 결정해요.
   *
   * `TextButton` 컴포넌트의 타입으로 정의된 `clear`, `arrow`, `underline` 세 가지를 제공해요.
   *
   * @default "underline"
   */
  variant?: "clear" | "arrow" | "underline";
}
```

---

# ListRow 영역 구성하기 (/tds-mobile/components/ListRow/list-row-components/)

# ListRow 영역 구성하기

이 문서를 읽고 나면,

- `ListRow`에서 사용할 수 있는 컴포넌트와 사용 방법을 이해할 수 있어요.
- `ListRow`의 `left`, `contents`, `right` 세 가지 영역에 위치할 수 있는 구성 요소를 이해하고 각 영역에 적합한 컴포넌트를 선택해 배치할 수 있어요.

## ListRow 구성요소 사용하기

### 아이콘 사용하기

`ListRow.AssetIcon` 컴포넌트는 리스트 항목에 아이콘을 추가해 콘텐츠의 성격을 표현할 때 사용해요. 이 컴포넌트들을 사용하면 항목의 중요한 특징을 직관적으로 전달할 수 있어요.

아이콘은 두 가지 방식으로 표시할 수 있어요. 디자인 시스템에서 제공하는 아이콘을 사용할 때는 `name` 속성을, 외부 이미지를 아이콘으로 사용할 때는 `url` 속성을 사용해요.
필요하면 `alt` 텍스트를 추가해 접근성을 높일 수 있어요.

#### 아이콘 모양 설정하기

`ListRow.AssetIcon` 컴포넌트는 `shape` 속성을 통해 다양한 스타일을 제공해요.

- `original`: 배경이 없는 기본 아이콘
- `squircle`: 스쿼클 배경이 있는 아이콘
- `card`: 카드 모양 배경이 있는 아이콘
- `circle`: 원형 배경이 있는 아이콘 (※ 레거시 옵션)

`ListRow.AssetIcon` 컴포넌트는 기본적으로 'small'과 'medium' 사이즈를 제공해요.
`variant="fill"` 속성을 설정하면 'xsmall', 'small', 'medium' 사이즈를 선택할 수 있어요.

**Example: AssetIcon**

```tsx
<List>
  }
    contents={}
  />
  }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />
  }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />

    }
    contents={}
  />
</List>
```

### 아이콘 버튼 사용하기

`ListRow.IconButton` 컴포넌트는 리스트 항목에 작은 버튼을 추가할 때 사용해요. 주로 설정, 즐겨찾기 추가 등 즉각적인 상호작용이 필요한 기능을 제공할 수 있어요.
버튼의 형태는 `variant` 속성을 통해 상황에 맞게 선택할 수 있어요.

- `fill`: 배경색이 있는 채워진 형태로, 주요 액션이나 강조가 필요할 때 사용해요.
- `clear`: 배경색이 없는 깔끔한 형태로, 간단한 액션이나 인터페이스를 깔끔하게 유지하고 싶을 때 사용해요.
- `border`: 테두리가 있는 형태로, 버튼의 영역을 시각적으로 구분하고 싶을 때 사용해요.

접근성을 고려해 `label` 속성을 통해 버튼의 용도를 설명할 수 있어요. 이는 스크린 리더 사용자들에게 버튼의 기능을 명확하게 전달해요.

**Example: IconButton**

```tsx
<List>
  }
    right={

    }
  />
  }
    right={

    }
  />
  }
    right={

    }
  />
</List>
```

### 이미지 사용하기

`ListRow.AssetImage` 컴포넌트는 실제 이미지나 썸네일을 표시할 때 사용해 리스트에 시각적인 정보를 더할 수 있어요.

이미지는 `shape` 속성을 통해 상황에 맞는 형태로 표현할 수 있어요.

- `original`: 원본 이미지
- `squircle`: 스쿼클 형태로 마스킹된 이미지
- `card`: 카드 형태로 마스킹된 이미지
- `square`: 정사각형으로 마스킹된 이미지
- `circle`: 원형으로 마스킹된 이미지

`ListRow.AssetImage` 컴포넌트는 'xsmall', 'small', 'medium'의 사이즈를 제공해요. 단, `square`, `circle`은 각각 52\*52, 40\*40의 고정 사이즈로 제공하고 있어요.
`original`은 아래와 같이 고정 사이즈로 제공돼요.

- `Image`: 높이 56 맞춤 고정 사이즈
- `2D Emoji`: 높이 24 맞춤 고정 사이즈
- `3D Emoji`: 높이 40 맞춤 고정 사이즈

배경이 없는 리소스일 경우 `backgroundColor` 속성을 함께 사용해 주세요.

**Example: AssetImage**

```tsx
<List>

    }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />
</List>
```

### 로띠 사용하기

`ListRow.AssetLottie` 컴포넌트를 사용하여 리스트 항목에 동적인 요소를 추가할 수 있어요. 주로 로딩 상태를 표현하거나 사용자의 주목을 끌어야 할 때 활용하면 좋아요.
<br/>`ListRow.AssetImage`와 동일하게 `shape` 속성을 사용할 수 있어요.

- `original`: 원본 로띠
- `squircle`: 스쿼클 배경이 있는 로띠
- `card`: 카드 모양 배경이 있는 로띠
- `square`: 정사각형 배경이 있는 로띠
- `circle`: 원형 배경이 있는 로띠

`ListRow.AssetLottie` 컴포넌트는 'xsmall', 'small', 'medium'의 사이즈를 제공해요. 단, `original`, `square`, `circle`은 각각 높이 40 맞춤, 52\*52, 40\*40의 고정 사이즈로 제공하고 있어요.

**Example: AssetLottie**

```tsx
<>

    }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />
  }
    contents={}
  />

    }
    contents={}
  />

    }
    contents={}
  />
</>
```

### 왼쪽 텍스트 사용하기

`ListRow.AssetText` 컴포넌트는 왼쪽에 순서나 간단한 텍스트를 표시할 때 사용해요.
`shape` 속성을 통해 `squircle`, `card` 형태를 사용할 수 있어요. 크기는 공통으로 'xsmall', 'small', 'medium' 사이즈를 제공해요.

**Example: AssetText**

```tsx
<List>
  <ListRow
    left={
      <ListRow.AssetText shape="squircle" size="xsmall">
        오늘
      </ListRow.AssetText>
    }
    contents={}
  />
  <ListRow
    left={
      <ListRow.AssetText shape="squircle" size="medium">
        오늘
      </ListRow.AssetText>
    }
    contents={}
  />
  <ListRow
    left={
      <ListRow.AssetText shape="card" size="xsmall">
        오늘
      </ListRow.AssetText>
    }
    contents={}
  />
  <ListRow
    left={
      <ListRow.AssetText shape="card" size="medium">
        오늘
      </ListRow.AssetText>
    }
    contents={}
  />
</List>
```

### 여러줄 텍스트 사용하기

`ListRow.Texts` 컴포넌트는 `type` 속성을 사용해 리스트 항목의 텍스트를 여러 줄로 나눠 표시하거나 시각적 계층을 조정할 수 있어요.
`type` 속성에 사용할 수 있는 값들은 일관된 네이밍 규칙을 따르고 있어요.

- 앞부분의 숫자(1Row, 2Row, 3Row)는 텍스트가 차지하는 줄 수를 나타내요.
- 앞부분에 'Right'가 붙으면 오른쪽 정렬, 없으면 왼쪽 정렬이에요.
- 마지막 알파벳(A, B, C...)은 텍스트의 스타일 세트를 나타내요. 각 세트는 글자 크기, 굵기, 색상 등의 조합으로 구성되어 있어요.

주요 정보를 표시할 때는 일반 텍스트 타입을 사용해요. 제목이나 설명과 같은 핵심 내용을 표현할 때 적합해요. 줄 수에 따라 다음과 같은 타입을 선택할 수 있어요.

- 1줄 텍스트: `1RowTypeA` ~ `1RowTypeC`
- 2줄 텍스트: `2RowTypeA` ~ `2RowTypeF`
- 3줄 텍스트: `3RowTypeA` ~ `3RowTypeF`

날짜, 시간, 가격 등의 보조 정보나 상태값을 표시할 때는 오른쪽 정렬 텍스트 타입을 사용해요. 이 타입들은 오른쪽에 깔끔하게 정렬되어 표시되며, 다음과 같은 옵션을 제공해요.

- 1줄 텍스트: `Right1RowTypeA` ~ `Right1RowTypeE`
- 2줄 텍스트: `Right2RowTypeA` ~ `Right2RowTypeE`

**Example: Texts**

```tsx
<List>
  } />
  } />
  } />
  } />
  } />
  } />
  } />
  } />
</List>
```

## ListRow 영역 활용하기

### 왼쪽 영역

`ListRow`의 왼쪽 영역은 사용자가 콘텐츠를 빠르게 인식할 수 있도록 도와주는 중요한 공간이에요.
이 영역에서는 `ListRow.AssetIcon`, `ListRow.AssetImage`, `ListRow.AssetLottie`, `ListRow.AssetText` 컴포넌트를 사용할 수 있어요.

**Example: LeftExample**

```tsx
<List>
  }
    contents={}
  />
  <ListRow
    left={
      <ListRow.AssetText shape="card" size="medium">
        오늘
      </ListRow.AssetText>
    }
    contents={}
  />
  }
    contents={}
  />

    }
    contents={}
  />
</List>
```

### contents 영역

`ListRow`의 `contents` 영역은 리스트 항목의 중앙에 위치해, 항목의 주요 텍스트 정보를 포함하는 공간이에요.
이 영역에서는 주로 `ListRow.Texts` 컴포넌트를 사용해 1줄, 2줄, 3줄 텍스트를 표현할 수 있어요.

**Example: ContentsExample**

```tsx
<List>
  } />
  } />
  } />
  } />
  } />
</List>
```

### 오른쪽 영역

`ListRow`의 오른쪽 영역은 사용자가 리스트 항목과 상호작용할 수 있는 다양한 요소를 배치할 수 있어요.
이 영역에서는 `ListRow.Texts`, `ListRow.IconButton` 컴포넌트를 사용하거나 `Switch`, `Badge` 같은 다른 컴포넌트와 조합할 수 있어요.
또한 `withArrow` prop을 사용해 화살표 아이콘을 표시할 수 있어요.

**Example: RightExample**

```tsx
<List>
  } />
  } />
  } />
  } right={} />
  }
    right={

    }
  />
  } withArrow={true} />
</List>
```

## 인터페이스

**Type: ListRowAssetIconProps**

```typescript
export interface ListRowAssetIconProps {
  /**
   * 아이콘의 모양을 설정해요.
   *
   * - `original`: 배경이 없는 기본 아이콘이에요.
   * - `squircle`: 스쿼클 형태의 아이콘이에요. 사이즈를 선택할 수 있어요.
   * - `card`: 카드 형태의 아이콘이에요. 사이즈를 선택할 수 있어요.
   * - `circle-background`: 원형 배경이 있는 아이콘이에요.
   * - `circle-masking`: 원형 마스킹이 있는 아이콘이에요.
   * @default squircle
   */
  shape?:
    "original" | "squircle" | "card" | "circle-background" | "circle-masking";
  /**
   * 아이콘의 대체 텍스트를 설정해요.
   */
  alt?: string;
  /**
   * 로깅을 위한 라벨을 설정해요.
   */
  dataLoggingLabel?: string;
  /**
   * 아이콘의 변형 스타일을 설정해요.
   * 기존의 Fill Icon을 대체하는 속성이에요.
   *
   * @default 'none'
   */
  variant?: "fill" | "none";
  /**
   * 아이콘의 크기를 설정해요.
   *
   * squircle-background 일 때만 유효해요.
   * @default medium
   */
  size?: "xsmall" | "small" | "medium";
  /**
   * shape가 card일 때 좌우 여백을 넣을지 결정해요.
   * true일 경우 size별로 매핑된 내부 여백 값이 적용돼요.
   *
   * @default false
   */
  paddingX?: boolean;
  /**
   * 액세서리(뱃지)를 설정해요.
   */
  acc?: ReactNode;

  /**
   * 액세서리의 위치를 지정해요.
   *
   * `top-right`, `bottom-right` 중 하나를 선택할 수 있어요.
   *
   * @default 'bottom-right'
   */
  accPosition?: "bottom-right" | "top-right";
  /**
   *
   * `circle`로 설정하면 액세서리에 테두리가 생겨요.
   *
   * @default 'none'
   */
  accMasking?: "circle" | "none";
}
```

**Type: ListRowIconButtonProps**

```typescript
export interface ListRowIconButtonProps {
  /**
   * 사용할 아이콘의 색상을 지정해요. 아이콘의 이름이 `-mono`로 끝나는 모노타입 아이콘을 사용할 때만 색상을 지정할 수 있어요.
   */
  color?: string;
  /**
   * `IconButton` 컴포넌트의 배경색을 지정해요.
   *
   * @default adaptive.greyOpacity100
   */
  bgColor?: string;
  /**
   * `IconButton` 컴포넌트의 형태를 결정해요.
   *
   * @default 'clear'
   */
  variant?: "fill" | "clear" | "border";
  /**
   * 이 값에 맞춰 아이콘의 크기를 변경해요. 예를 들어 이 값이 24라면, 24px이 크기로 적용돼요.
   *
   * @default 24
   */
  iconSize?: number;
  /**
   * button 태그의 `aria-label` 속성을 결정해요.
   */
  label?: string;
}
```

**Type: ListRowAssetImageProps**

```typescript
export interface ListRowAssetImageProps {
  /**
   * 이미지의 소스를 설정해요.
   */
  src: string;
  /**
   * 이미지의 사이즈를 설정해요.
   *
   * @default 'small'
   */
  size?: "xsmall" | "small" | "medium";
  /**
   * 이미지의 모양을 설정해요.
   *
   * @default 'squircle'
   */
  shape?: "square" | "squircle" | "circle" | "original" | "card";
  /**
   * shape가 card일 때 좌우 여백을 넣을지 결정해요.
   * true일 경우 size별로 매핑된 내부 여백 값이 적용돼요.
   *
   * @default false
   */
  paddingX?: boolean;
  /**
   * 액세서리(뱃지)를 설정해요.
   */
  acc?: ReactNode;

  /**
   * 액세서리의 위치를 지정해요.
   *
   * `top-right`, `bottom-right` 중 하나를 선택할 수 있어요.
   *
   * @default 'bottom-right'
   */
  accPosition?: "bottom-right" | "top-right";
  /**
   *
   * `circle`로 설정하면 액세서리에 테두리가 생겨요.
   *
   * @default 'none'
   */
  accMasking?: "circle" | "none";
}
```

**Type: ListRowAssetLottieProps**

```typescript
export interface ListRowAssetLottieProps {
  /**
   * 로티 아이콘의 소스를 설정해요.
   */
  src: string;
  /**
   * 로띠의 사이즈를 설정해요.
   *
   * @default 'small'
   */
  size?: "xsmall" | "small" | "medium";
  /**
   * 로띠의 배경색을 설정해요. shape이 original인 경우에는 적용되지 않아요.
   *
   * @default adaptive.greyOpacity100
   */
  backgroundColor?: string;
  /**
   * 로띠의 모양을 설정해요.
   * @default 'squircle'
   */
  shape?: "card" | "square" | "squircle" | "circle" | "original";
  /**
   * shape가 card일 때 좌우 여백을 넣을지 결정해요.
   * true일 경우 size별로 매핑된 내부 여백 값이 적용돼요.
   *
   * @default false
   */
  paddingX?: boolean;
  /**
   * 액세서리(뱃지)를 설정해요.
   */
  acc?: ReactNode;

  /**
   * 액세서리의 위치를 지정해요.
   *
   * `top-right`, `bottom-right` 중 하나를 선택할 수 있어요.
   *
   * @default 'bottom-right'
   */
  accPosition?: "bottom-right" | "top-right";
  /**
   *
   * `circle`로 설정하면 액세서리에 테두리가 생겨요.
   *
   * @default 'none'
   */
  accMasking?: "circle" | "none";
}
```

**Type: ListRowAssetTextProps**

```typescript
export interface ListRowAssetTextProps {
  /**
   * 텍스트의 사이즈를 설정해요.
   *
   * @default 'small'
   */
  size?: "xsmall" | "small" | "medium";
  /**
   * 텍스트의 배경색을 설정해요.
   *
   * @default adaptive.greyOpacity100
   */
  backgroundColor?: string;
  /**
   * 텍스트의 색상을 설정해요.
   *
   * @default adaptive.blue500
   */
  color?: string;
  /**
   * 텍스트의 내용을 설정해요.
   */
  children: ReactNode;
  /**
   * 텍스트의 모양을 설정해요.
   */
  shape: "card" | "squircle";
  /**
   * shape가 card일 때 좌우 여백을 넣을지 결정해요.
   * true일 경우 size별로 매핑된 내부 여백 값이 적용돼요.
   *
   * @default false
   */
  paddingX?: boolean;
  /**
   * 액세서리(뱃지)를 설정해요.
   */
  acc?: ReactNode;

  /**
   * 액세서리의 위치를 지정해요.
   *
   * `top-right`, `bottom-right` 중 하나를 선택할 수 있어요.
   *
   * @default 'bottom-right'
   */
  accPosition?: "bottom-right" | "top-right";
  /**
   *
   * `circle`로 설정하면 액세서리에 테두리가 생겨요.
   *
   * @default 'none'
   */
  accMasking?: "circle" | "none";
}
```

**Type: ListRowTextsProps**

```typescript
export interface ListRowTextsProps {
  /**
   * 텍스트의 타입을 설정해요.
   *
   * - 1줄 텍스트: `1RowTypeA` ~ `1RowTypeC`, `Right1RowTypeA` ~ `Right1RowTypeE`
   * - 2줄 텍스트: `2RowTypeA` ~ `2RowTypeF`, `Right2RowTypeA` ~ `Right2RowTypeE`
   * - 3줄 텍스트: `3RowTypeA` ~ `3RowTypeF`
   */
  type?:
    | "1RowTypeA"
    | "1RowTypeB"
    | "1RowTypeC"
    | "Right1RowTypeA"
    | "Right1RowTypeB"
    | "Right1RowTypeC"
    | "Right1RowTypeD"
    | "Right1RowTypeE"
    | "2RowTypeA"
    | "2RowTypeB"
    | "2RowTypeC"
    | "2RowTypeD"
    | "2RowTypeE"
    | "2RowTypeF"
    | "Right2RowTypeA"
    | "Right2RowTypeB"
    | "Right2RowTypeC"
    | "Right2RowTypeD"
    | "Right2RowTypeE"
    | "3RowTypeA"
    | "3RowTypeB"
    | "3RowTypeC"
    | "3RowTypeD"
    | "3RowTypeE"
    | "3RowTypeF";
  /**
   * 상단 텍스트를 설정해요.
   */
  top?: "ReactElement | string";
  /**
   * 중간 텍스트를 설정해요. (3Row 타입인 경우)
   */
  middle?: "ReactElement | string";
  /**
   * 하단 텍스트를 설정해요. (2Row, 3Row 타입인 경우)
   */
  bottom?: "ReactElement | string";
  /**
   * 위쪽 여백을 설정해요.
   */
  marginTop?: number;
}
```

---

# ListRow 이해하기 (/tds-mobile/components/ListRow/list-row-overview/)

# ListRow 이해하기

[Image: ListRow thumbnail - list-row/components/Thumbnail-ListRow.png]

이 문서를 읽고 나면

- `ListRow` 컴포넌트의 전반적인 구성 요소와 그 역할에 대해 이해할 수 있어요.
- 다양한 스타일 옵션을 활용해 `ListRow`의 외형과 동작을 시각적으로 조정할 수 있어요.
- `ListRow`의 로딩 상태를 표시하고, 사용자 경험을 개선할 수 있어요.

[Preview: Basic]

## 이해하기

`ListRow` 컴포넌트는 리스트 형태의 UI를 구성할 때 사용해요. `left`, `contents`, `right` 세 영역으로 나뉘어 있으며, 각 영역에 아이콘, 텍스트, 이미지를 추가해 직관적인 리스트 아이템을 만들 수 있어요.
또한 터치 효과와 화살표 속성으로 사용자가 리스트 아이템의 동작을 쉽게 예측할 수 있고, 비활성화 속성을 사용해 특정 항목을 비활성화할 수도 있어요.
이를 통해 상황에 맞춰 다양한 리스트 UI를 구성할 수 있어요.

## ListRow의 기본 구조

`ListRow` 컴포넌트는 기본적으로 세 가지 주요 부분인 `left`, `contents`, `right`로 나뉘어 있어요.
각 영역에 맞는 내부 컴포넌트들을 적절히 배치해 사용자에게 적합한 리스트 아이템을 만들 수 있게 도와줘요.

- `left`: 컴포넌트 가장 왼쪽에 위치해 아이콘이나 이미지를 배치해 항목을 직관적으로 이해할 수 있게 돕는 영역이에요.
- `contents`: 컴포넌트의 중앙에 위치해 주요 텍스트 정보가 들어가는 영역으로 다양한 텍스트 레이아웃을 선택할 수 있어요.
- `right`: 컴포넌트의 가장 오른쪽에 위치해 부가적인 정보나 상호작용 요소를 배치하는 영역이에요.

각 영역의 구체적인 활용 예시는 [ListRow 영역 구성하기](/components/ListRow/list-row-components) 페이지를 확인해 주세요.

**Example: ComponentExample**

```tsx
}
  contents={}
  right={
    <Button color="primary" size="small" variant="weak">
      Button
    </Button>
  }
/>
```

## 스타일 적용하기

### 구분선 사용하기

`border` 속성은 리스트 항목 위에 구분선을 추가하는 옵션이에요. 기본적으로 두 가지 스타일이 제공돼요.

- `indented`: 왼쪽에 들여쓰기가 적용된 구분선이에요. 주로 리스트 항목을 구분하기 위해 사용해요.
- `none`: 구분선이 없는 스타일이예요. 다른 리스트 항목과 연결된 느낌을 주고 싶을 때 사용해요.

**Example: BorderStyle**

```tsx
} />
```

### 위 아래 여백 조절하기

`verticalPadding` 속성은 `ListRow` 컴포넌트의 상하 여백을 조절해 리스트 항목 간 간격을 다양하게 설정할 수 있어요.
이 속성을 통해 컴포넌트가 차지하는 세로 공간을 조정해 UI의 밀도와 시각적 여유를 조절할 수 있어요. 선택 가능한 옵션은 `small`, `medium`, `large`, `xlarge`로, 각 옵션에 따라 여백의 크기가 다르게 적용돼요.

**Example: VerticalPaddingStyle**

```tsx
<List>
  } />
  } />
  } />
  } />
</List>
```

### 양옆 여백 조절하기

`horizontalPadding` 속성은 `ListRow` 컴포넌트의 좌우 여백을 조절할 수 있어요.
이 속성을 활용하면 콘텐츠와 화면 가장자리 사이의 간격을 조절해 리스트의 시각적 밀도를 조정할 수 있어요. 선택 가능한 옵션은 `small`, `medium`로, 각 옵션에 따라 여백의 크기가 다르게 적용돼요.

**Example: HorizontalPaddingStyle**

```tsx
<List>
  } />
  }
  />
</List>
```

### 비활성화하기

`disabled` 속성을 설정하면 리스트 항목을 비활성화시켜 클릭이나 상호작용을 막을 수 있어요.
`disabledStyle` 속성을 사용해 비활성화된 항목의 스타일을 선택해요. 기본적으로 두 가지 스타일이 제공돼요.

- `type1`: 기본 비활성화 스타일로, 연한 흰색 배경이 적용돼요.
- `type2`: 기본 비활성화 스타일에 추가로 회색 배경이 덧입혀져 더 진하게 표시돼요. 선택 불가 상태임을 더 명확하게 전달하고 싶을 때 적합해요.

**Example: DisabledStyle**

```tsx
<List style={{ position: 'relative', zIndex: 1 }}>
  }
    contents={}
    right={<Button size="small">Button</Button>}
  />
  }
    contents={}
    right={<Button size="small">Button</Button>}
  />
</List>
```

### 터치 이벤트로 시각적인 반응 제공하기

`ListRow`는 `onClick` 핸들러가 있거나 `withTouchEffect` 속성을 직접 설정하면 터치 효과가 적용돼요.
사용자가 리스트 항목을 터치할 때 시각적인 반응을 제공해서 더 직관적인 인터페이스를 만들 수 있어요.

**Example: TouchEffectStyle**

```tsx
<List>
  } withTouchEffect />
  } onClick={() => {}} />
</List>
```

### 시각적으로 강조하기

`ListRow`의 `ref`를 사용해서 리스트 항목을 시각적으로 강조할 수 있어요. 두 가지 효과를 활용하면 사용자의 주의를 더 효과적으로 끌 수 있어요.

- `shine`: 항목을 가로지르는 반짝임 효과를 보여줘요. 새로운 항목이 추가되었거나 중요한 변경사항을 강조하고 싶을 때 유용해요.
- `blink`: 항목 전체가 깜빡이는 효과를 보여줘요. 사용자의 주의를 끌어야 할 때 활용할 수 있어요.

**Example: VisualEffects**

```tsx
function VisualEffects() {
  const shineRef = React.useRef<ListRowRef>(null);
  const blinkRef = React.useRef<ListRowRef>(null);
  return (
    <List>
      }
        right={
          <Button
            size="small"
            onClick={() => {
              shineRef.current?.shine(2);
            }}
          >
            Shine
          </Button>
        }
      />
      }
        right={
          <Button
            size="small"
            onClick={() => {
              blinkRef.current?.blink(1.5);
            }}
          >
            Blink
          </Button>
        }
      />
    </List>
  );
}
```

## 로딩 상태 표시하기

`ListRow.Loader` 컴포넌트를 사용하면 데이터가 로딩되는 동안 스켈레톤 UI를 표시할 수 있어요.
사용자에게 콘텐츠가 곧 로드될 것임을 시각적으로 알려주어 더 나은 사용자 경험을 제공할 수 있어요.
로더는 실제 `ListRow`와 동일한 레이아웃을 가지고 있어 자연스러운 전환 효과를 만들 수 있어요.

**Example: Loader**

```tsx

```

## 인터페이스

**Type: ListRowProps**

```typescript
export interface ListRowProps {
  /**
   * `ListRow` 컴포넌트의 구분선 스타일을 설정해요.
   *
   * - `indented`: 왼쪽에 들여쓰기가 적용된 구분선이에요.
   * - `none`: 구분선이 없는 스타일이에요.
   * @default indented
   */
  border?: "indented" | "none";
  /**
   * `ListRow` 컴포넌트의 비활성화 상태를 설정해요.
   * @default false
   */
  disabled?: boolean;
  /**
   * 비활성화된 `ListRow` 컴포넌트의 스타일을 설정해요.
   *
   * - `type1`: 연한 배경색이 적용된 스타일이에요.
   * - `type2`: 진한 배경색이 적용된 스타일이에요.
   * @default type1
   */
  disabledStyle?: "type1" | "type2";
  /**
   * `ListRow` 컴포넌트의 상하 여백을 설정해요.
   *
   * - `small`: 작은 여백이에요. (8px)
   * - `medium`: 중간 크기의 여백이에요. (12px)
   * - `large`: 큰 여백이에요. (16px)
   * - `xlarge`: 가장 큰 여백이에요. (24px)
   * @default medium
   */
  verticalPadding?: "small" | "medium" | "large" | "xlarge";
  /**
   * `ListRow` 컴포넌트의 좌우 여백을 설정해요.
   *
   * - `small`: 작은 여백이에요. (20px)
   * - `medium`: 중간 크기의 여백이에요. (24px)
   *
   * @default medium
   */
  horizontalPadding?: "small" | "medium";
  /**
   * `ListRow` 컴포넌트의 왼쪽 영역에 들어갈 요소를 설정해요.
   */
  left?: ReactNode;
  /**
   * 왼쪽 영역 요소의 수직 정렬을 설정해요.
   * @default center
   */
  leftAlignment?: "top" | "center";
  /**
   * `ListRow` 컴포넌트의 중앙 영역에 들어갈 요소를 설정해요.
   */
  contents?: ReactNode;
  /**
   * `ListRow` 컴포넌트의 오른쪽 영역에 들어갈 요소를 설정해요.
   */
  right?: ReactNode;
  /**
   * 오른쪽 영역 요소의 수직 정렬을 설정해요.
   * @default center
   */
  rightAlignment?: "top" | "center";
  /**
   * 오른쪽 끝에 화살표 아이콘을 표시할지 설정해요.
   * @default false
   */
  withArrow?: boolean;
  /**
   * 터치 시 시각적 효과를 표시할지 설정해요.
   * @default false
   */
  withTouchEffect?: boolean;
}
```

**Type: ListRowLoaderProps**

```typescript
export interface ListRowLoaderProps {
  /**
   * `ListRowLoader` 컴포넌트의 로더 모양을 설정해요.
   *
   * - `square`: 정사각형 모양의 로더예요.
   * - `circle`: 원형 모양의 로더예요.
   * - `bar`: 막대 모양의 로더예요.
   * @default square
   */
  type?: "square" | "circle" | "bar";
  /**
   * `ListRowLoader` 컴포넌트의 상하 여백을 설정해요.
   *
   * - `extraSmall`: 가장 작은 여백이에요.
   * - `small`: 작은 여백이에요.
   * - `medium`: 중간 크기의 여백이에요.
   * - `large`: 큰 여백이에요.
   * @default medium
   */
  verticalPadding?: "large" | "medium" | "small" | "extraSmall";
}
```

---

# 이전 ListRow 확인하기 (/tds-mobile/components/ListRow/ListRowLegacy/list-row-legacy/)

# 이전 ListRow 확인하기

이 문서를 읽고 나면,

- `ListRow`에서 사용할 수 있는 컴포넌트와 사용 방법을 이해할 수 있어요.
- `ListRow`의 `left`, `contents`, `right` 세 가지 영역에 위치할 수 있는 구성 요소를 이해하고 각 영역에 적합한 컴포넌트를 선택해 배치할 수 있어요.

## ListRow 구성요소 사용하기

### 아이콘 사용하기

`ListRow.Icon`과 `ListRow.FillIcon` 컴포넌트는 리스트 항목에 아이콘을 추가해 콘텐츠의 성격을 표현할 때 사용해요. 이 컴포넌트들을 사용하면 항목의 중요한 특징을 직관적으로 전달할 수 있어요.

아이콘은 두 가지 방식으로 표시할 수 있어요. 디자인 시스템에서 제공하는 아이콘을 사용할 때는 `name` 속성을, 외부 이미지를 아이콘으로 사용할 때는 `url` 속성을 사용해요.
필요하면 `alt` 텍스트를 추가해 접근성을 높일 수 있어요.

#### 아이콘 모양 설정하기

`ListRow.Icon`과 `ListRow.FillIcon` 컴포넌트는 `shape` 속성을 통해 다양한 스타일을 제공해요.

**`ListRow.Icon` 컴포넌트**

- `no-background`: 배경이 없는 기본 아이콘
- `squircle-background`: 스쿼클 배경이 있는 아이콘
- `circle-background`: 원형 배경이 있는 아이콘
- `circle-masking`: 이미지를 원형으로 마스킹한 아이콘

**`ListRow.FillIcon` 컴포넌트**

- `default`: 배경이 없는 기본 아이콘
- `squircle`: 스쿼클 형태로 마스킹된 아이콘
- `circle-background`: 원형 배경이 있는 아이콘
- `circle-masking`: 아이콘을 원형으로 마스킹한 아이콘

`ListRow.Icon` 컴포넌트의 `squircle-background`와 `ListRow.FillIcon` 컴포넌트의 `squircle`에서는 `size` 속성으로 'medium'과 'large' 크기를 선택할 수 있어요.

#### Non-Fill Icon 사용하기

**Example: Icon**

```tsx
<List>
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
</List>
```

#### Fill Icon 사용하기

**Example: FillIcon**

```tsx
<List>
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
</List>
```

### 아이콘 버튼 사용하기

`ListRow.IconButton` 컴포넌트는 리스트 항목에 작은 버튼을 추가할 때 사용해요. 주로 설정, 즐겨찾기 추가 등 즉각적인 상호작용이 필요한 기능을 제공할 수 있어요.
버튼의 형태는 `variant` 속성을 통해 상황에 맞게 선택할 수 있어요.

- `fill`: 배경색이 있는 채워진 형태로, 주요 액션이나 강조가 필요할 때 사용해요.
- `clear`: 배경색이 없는 깔끔한 형태로, 간단한 액션이나 인터페이스를 깔끔하게 유지하고 싶을 때 사용해요.
- `border`: 테두리가 있는 형태로, 버튼의 영역을 시각적으로 구분하고 싶을 때 사용해요.

접근성을 고려해 `label` 속성을 통해 버튼의 용도를 설명할 수 있어요. 이는 스크린 리더 사용자들에게 버튼의 기능을 명확하게 전달해요.

**Example: IconButton**

```tsx
<List>
  }
    right={

    }
  />
  }
    right={

    }
  />
  }
    right={

    }
  />
</List>
```

### 이미지 사용하기

`ListRow.Image` 컴포넌트는 실제 이미지나 썸네일을 표시할 때 사용해 리스트에 시각적인 정보를 더할 수 있어요.
이미지는 `type` 속성을 통해 상황에 맞는 형태로 표현할 수 있어요. 기본 이미지 형태인 `default`부터 정사각형 형태의 `square`, 직사각형 형태의 `rectangle`과 그보다 작은 `rectangle-small`, 프로필 이미지에 적합한 `circle`과 `circle-small`, 그리고 3D 이모지 표현에 최적화된 `3d-emoji`까지 다양한 옵션을 제공해요.

**Example: Image**

```tsx
<List>
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />
  }
    contents={}
  />

  }
    contents={}
  />
</List>
```

### 로띠 사용하기

로띠 애니메이션을 통해 리스트 항목에 동적인 요소를 추가할 수 있어요. 주로 로딩 상태를 표현하거나 사용자의 주목을 끌어야 할 때 활용하면 좋아요.
로띠를 사용하려면 `Asset.Lottie` 컴포넌트를 `ListRow.ImageContainer`로 감싸서 사용해야 해요.
`ListRow.Image`와 동일하게 `type` 속성을 사용할 수 있어요. `default`, `square`, `rectangle`, `circle` 등의 타입을 지정해 로띠 애니메이션의 컨테이너 형태를 자유롭게 설정할 수 있어요.

**Example: Lottie**

```tsx
<ListRow
  left={<ListRow.ImageContainer type="circle"></ListRow.ImageContainer>}
  contents="Lottie (Rectangle)"
/>
```

### 왼쪽 텍스트 사용하기

`ListRow.LeftText` 컴포넌트는 왼쪽에 순서나 간단한 텍스트를 표시할 때 사용해요. 두 가지 형태를 지원해요.

- `default`: 굵은 글씨체로 강조된 텍스트로 순서나 중요 코드에 활용할 수 있어요.
- `border`: 원형 테두리가 있는 텍스트로 상태를 표시하거나, 카테고리를 보여줄 수 있어요.

  **Example: LeftText**

```tsx
<List>
  <ListRow left={<ListRow.LeftText>01.01</ListRow.LeftText>} contents={} />
  <ListRow
    left={<ListRow.LeftText color={colors.blue700}>1</ListRow.LeftText>}
    contents={}
  />
  <ListRow
    left={
      <ListRow.LeftText color={colors.blue500} type="border">
        김
      </ListRow.LeftText>
    }
    contents={}
  />
</List>
```

### 여러줄 텍스트 사용하기

`ListRow.Texts` 컴포넌트는 `type` 속성을 사용해 리스트 항목의 텍스트를 여러 줄로 나눠 표시하거나 시각적 계층을 조정할 수 있어요.
`type` 속성에 사용할 수 있는 값들은 일관된 네이밍 규칙을 따르고 있어요.

- 앞부분의 숫자(1Row, 2Row, 3Row)는 텍스트가 차지하는 줄 수를 나타내요.
- 앞부분에 'Right'가 붙으면 오른쪽 정렬, 없으면 왼쪽 정렬이에요.
- 마지막 알파벳(A, B, C...)은 텍스트의 스타일 세트를 나타내요. 각 세트는 글자 크기, 굵기, 색상 등의 조합으로 구성되어 있어요.

주요 정보를 표시할 때는 일반 텍스트 타입을 사용해요. 제목이나 설명과 같은 핵심 내용을 표현할 때 적합해요. 줄 수에 따라 다음과 같은 타입을 선택할 수 있어요.

- 1줄 텍스트: `1RowTypeA` ~ `1RowTypeC`
- 2줄 텍스트: `2RowTypeA` ~ `2RowTypeF`
- 3줄 텍스트: `3RowTypeA` ~ `3RowTypeF`

날짜, 시간, 가격 등의 보조 정보나 상태값을 표시할 때는 오른쪽 정렬 텍스트 타입을 사용해요. 이 타입들은 오른쪽에 깔끔하게 정렬되어 표시되며, 다음과 같은 옵션을 제공해요.

- 1줄 텍스트: `Right1RowTypeA` ~ `Right1RowTypeE`
- 2줄 텍스트: `Right2RowTypeA` ~ `Right2RowTypeE`

**Example: Texts**

```tsx
<List>
  } />
  } />
  } />
  } />
  } />
  } />
  } />
  } />
</List>
```

## ListRow 영역 활용하기

### 왼쪽 영역

`ListRow`의 왼쪽 영역은 사용자가 콘텐츠를 빠르게 인식할 수 있도록 도와주는 중요한 공간이에요.
이 영역에서는 `ListRow.Icon`, `ListRow.LeftText`, `ListRow.Image`, `ListRow.ImageContainer` 컴포넌트를 사용할 수 있어요.

**Example: LeftExample**

```tsx
<List>
  }
    contents={}
  />
  <ListRow
    left={
      <ListRow.LeftText color={colors.blue500} type="border">
        김
      </ListRow.LeftText>
    }
    contents={}
  />
  }
    contents={}
  />
  <ListRow
    left={
      <ListRow.ImageContainer type="circle">

      </ListRow.ImageContainer>
    }
    contents="Lottie"
  />
</List>
```

### contents 영역

`ListRow`의 `contents` 영역은 리스트 항목의 중앙에 위치해, 항목의 주요 텍스트 정보를 포함하는 공간이에요.
이 영역에서는 주로 `ListRow.Texts` 컴포넌트를 사용해 1줄, 2줄, 3줄 텍스트를 표현할 수 있어요.

**Example: ContentsExample**

```tsx
<List>
  } />
  } />
  } />
  } />
  } />
</List>
```

### 오른쪽 영역

`ListRow`의 오른쪽 영역은 사용자가 리스트 항목과 상호작용할 수 있는 다양한 요소를 배치할 수 있어요.
이 영역에서는 `ListRow.Texts`, `ListRow.IconButton` 컴포넌트를 사용하거나 `Switch`, `Badge` 같은 다른 컴포넌트와 조합할 수 있어요.
또한 `withArrow` prop을 사용해 화살표 아이콘을 표시할 수 있어요.

**Example: RightExample**

```tsx
<List>
  } />
  } />
  } />
  } right={} />
  }
    right={

    }
  />
  } withArrow={true} />
</List>
```

## 인터페이스

**Type: ListRowIconProps**

```typescript
export interface ListRowIconProps {
  /**
   * 아이콘의 모양을 설정해요.
   *
   * - `no-background`: 기본 크기의 아이콘이에요.
   * - `squircle-background`: 스쿼클 배경이 있는 아이콘이에요. 사이즈를 선택할 수 있어요.
   * - `circle-background`: 원형 배경이 있는 아이콘이에요.
   * - `circle-masking`: 원형으로 마스킹된 아이콘이에요.
   * @default no-background
   */
  shape?:
    | "no-background"
    | "squircle-background"
    | "circle-background"
    | "circle-masking";
  /**
   * 아이콘의 대체 텍스트를 설정해요.
   */
  alt?: string;
  /**
   * 로깅을 위한 라벨을 설정해요.
   */
  dataLoggingLabel?: string;

  /**
   * 아이콘의 크기를 설정해요.
   *
   * squircle-background 일 때만 유효해요.
   * @default medium
   */
  size?: "medium" | "large";
}
```

**Type: ListRowFillIconProps**

```typescript
export interface ListRowFillIconProps {
  /**
   * 아이콘의 모양을 설정해요.
   *
   * - `default`: 기본 크기의 아이콘이에요.
   * - `squircle`: 스쿼클 형태로 마스킹된 아이콘이에요. 사이즈를 선택할 수 있어요.
   * - `circle-background`: 원형 배경이 있는 아이콘이에요.
   * - `circle-masking`: 원형으로 마스킹된 아이콘이에요.
   * @default default
   */
  shape?: "default" | "squircle" | "circle-background" | "circle-masking";
  /**
   * 아이콘의 대체 텍스트를 설정해요.
   */
  alt?: string;
  /**
   * 로깅을 위한 라벨을 설정해요.
   */
  dataLoggingLabel?: string;

  /**
   * 아이콘의 크기를 설정해요.
   *
   * squircle 일 때만 유효해요.
   * @default medium
   */
  size?: "medium" | "large";
}
```

**Type: ListRowIconButtonProps**

```typescript
export interface ListRowIconButtonProps {
  /**
   * 사용할 아이콘의 색상을 지정해요. 아이콘의 이름이 `-mono`로 끝나는 모노타입 아이콘을 사용할 때만 색상을 지정할 수 있어요.
   */
  color?: string;
  /**
   * `IconButton` 컴포넌트의 배경색을 지정해요.
   *
   * @default adaptive.greyOpacity100
   */
  bgColor?: string;
  /**
   * `IconButton` 컴포넌트의 형태를 결정해요.
   *
   * @default 'clear'
   */
  variant?: "fill" | "clear" | "border";
  /**
   * 이 값에 맞춰 아이콘의 크기를 변경해요. 예를 들어 이 값이 24라면, 24px이 크기로 적용돼요.
   *
   * @default 24
   */
  iconSize?: number;
  /**
   * button 태그의 `aria-label` 속성을 결정해요.
   */
  label?: string;
}
```

**Type: ListRowImageContainerProps**

```typescript
export interface ListRowImageContainerProps {
  /**
   * 이미지 컨테이너의 타입을 설정해요.
   *
   * - `default`: 기본 스타일이에요.
   * - `square`: 정사각형 스타일이에요.
   * - `rectangle`: 직사각형 스타일이에요.
   * - `rectangle-small`: 작은 직사각형 스타일이에요.
   * - `circle`: 원형 스타일이에요.
   * - `circle-small`: 작은 원형 스타일이에요.
   * - `3d-emoji`: 3D 이모지 스타일이에요.
   * @default default
   */
  type?:
    | "default"
    | "square"
    | "rectangle"
    | "rectangle-small"
    | "circle"
    | "circle-small"
    | "3d-emoji";
  /**
   * 테두리 표시 여부를 설정해요.
   * @default false
   */
  border?: boolean;
}
```

**Type: ListRowImageProps**

```typescript
export interface ListRowImageProps {
  /**
   * 이미지 컨테이너의 타입을 설정해요.
   * @default default
   */
  type?:
    | "default"
    | "square"
    | "rectangle"
    | "rectangle-small"
    | "circle"
    | "circle-small"
    | "3d-emoji";
  /**
   * 테두리 표시 여부를 설정해요.
   * @default false
   */
  border?: boolean;
  /**
   * 컨테이너의 스타일을 설정해요.
   */
  containerStyle?: CSSProperties;
}
```

**Type: ListRowLeftTextProps**

```typescript
export interface ListRowLeftTextProps {
  /**
   * 텍스트의 타입을 설정해요.
   *
   * - `default`: 기본 스타일이에요.
   * - `border`: 테두리가 있는 스타일이에요.
   * @default default
   */
  type?: "default" | "border";
  /**
   * 위쪽 여백을 설정해요.
   */
  marginTop?: number;
}
```

**Type: ListRowTextsProps**

```typescript
export interface ListRowTextsProps {
  /**
   * 텍스트의 타입을 설정해요.
   *
   * - 1줄 텍스트: `1RowTypeA` ~ `1RowTypeC`, `Right1RowTypeA` ~ `Right1RowTypeE`
   * - 2줄 텍스트: `2RowTypeA` ~ `2RowTypeF`, `Right2RowTypeA` ~ `Right2RowTypeE`
   * - 3줄 텍스트: `3RowTypeA` ~ `3RowTypeF`
   */
  type?:
    | "1RowTypeA"
    | "1RowTypeB"
    | "1RowTypeC"
    | "Right1RowTypeA"
    | "Right1RowTypeB"
    | "Right1RowTypeC"
    | "Right1RowTypeD"
    | "Right1RowTypeE"
    | "2RowTypeA"
    | "2RowTypeB"
    | "2RowTypeC"
    | "2RowTypeD"
    | "2RowTypeE"
    | "2RowTypeF"
    | "Right2RowTypeA"
    | "Right2RowTypeB"
    | "Right2RowTypeC"
    | "Right2RowTypeD"
    | "Right2RowTypeE"
    | "3RowTypeA"
    | "3RowTypeB"
    | "3RowTypeC"
    | "3RowTypeD"
    | "3RowTypeE"
    | "3RowTypeF";
  /**
   * 상단 텍스트를 설정해요.
   */
  top?: "ReactElement | string";
  /**
   * 중간 텍스트를 설정해요. (3Row 타입인 경우)
   */
  middle?: "ReactElement | string";
  /**
   * 하단 텍스트를 설정해요. (2Row, 3Row 타입인 경우)
   */
  bottom?: "ReactElement | string";
  /**
   * 위쪽 여백을 설정해요.
   */
  marginTop?: number;
}
```

---

# Loader (/tds-mobile/components/loader/)

# Loader

`Loader` 컴포넌트는 사용자가 기다리는 동안 콘텐츠가 로드 중임을 시각적으로 알려줘요. 데이터를 불러오거나 작업이 진행 중일 때 사용자에게 피드백을 제공하기 위해 활용해요.

[Preview: Basic]

## 사용법

### 크기 설정하기

`Loader` 컴포넌트의 크기는 `size` 속성을 사용해 설정할 수 있어요. 사용할 수 있는 값은 `small`, `medium`, `large`이며, 기본값은 `medium`이에요.

**Example: Size**

```tsx
<div style={{ display: "flex", gap: 20, alignItems: "center" }}></div>
```

### 타입 설정하기

`Loader` 컴포넌트의 타입은 `type` 속성을 사용해 설정할 수 있어요. 사용할 수 있는 값은 `primary`, `dark`, `light`이며, 기본값은 `primary`이에요.

특히 `light` 타입은 어두운 배경에서 사용하기 적합해요.

**Example: Type**

```tsx
<div style={{ display: "flex", gap: "16px", alignItems: "center" }}></div>
```

### 레이블 추가하기

`Loader` 컴포넌트 아래에 텍스트를 추가하려면 `label` 속성을 사용하면 돼요. 로딩 중임을 텍스트로도 알려주거나, 로딩 중에 이루어지는 작업을 설명할 수 있어요.

**Example: WithLabel**

```tsx

```

## 인터페이스

**Type: LoaderProps**

```typescript
export interface LoaderProps {
  /**
   * `Loader` 컴포넌트의 크기를 지정해요.
   *
   * @default 'medium'
   */
  size?: "small" | "medium" | "large";

  /**
   * `Loader` 컴포넌트의 타입을 지정해요. 타입은 `primary`, `dark`, `light` 중 하나를 선택할 수 있어요.
   *
   * 각 타입별 색상이 달라요.
   *
   * @default 'primary'
   */
  type?: "primary" | "dark" | "light";

  /**
   * `Loader` 컴포넌트 하단에 표시될 텍스트를 지정해요.
   *
   * 로딩 상태에 대한 설명이나 진행 중인 작업을 설명하는 텍스트를 표시할 수 있으며, 여러 줄의 텍스트도 지원해요.
   */
  label?: string;

  /**
   * `Loader` 컴포넌트의 스타일을 직접 지정해요.
   */
  style?: CSSProperties;

  /**
   * `Loader` 컴포넌트의 `className`을 지정해요.
   */
  className?: string;

  /**
   * `Loader` 컴포넌트의 고유 id를 지정해요.
   */
  id?: string;
}
```

---

# Menu (/tds-mobile/components/menu/)

# Menu

`Menu` 컴포넌트는 드롭다운 메뉴를 사용해 항목을 선택하거나 상태를 확인하고 바꿀 수 있어요.
여러 옵션을 정리해서 보여주고, 설정 화면이나 작업 리스트처럼 다양한 곳에서 활용할 수 있어요.
버튼 클릭이나 입력과 같은 사용자 동작에 따라 메뉴를 열고 닫을 수 있어서 동적인 UI를 쉽게 구현할 수 있어요.

[Preview: Basic]

## 드롭다운 메뉴 만들기

드롭다운 메뉴를 사용하면 여러 옵션을 깔끔하게 나열하고, 사용자가 원하는 항목을 선택할 수 있어요.
`Menu.Dropdown` 컴포넌트를 사용해서 기본 드롭다운 메뉴를 생성할 수 있어요.

- `Menu.Dropdown`: 드롭다운 컨테이너 역할을 해요. `header` 속성을 사용해서 메뉴 상단에 제목을 추가할 수 있어요.
- `Menu.Header`: 메뉴의 제목을 나타내요. 드롭다운 상단에 위치하며, 제목 텍스트를 전달할 수 있어요.
- `Menu.DropdownItem`: 드롭다운 메뉴의 개별 항목을 나타내요. 사용자가 선택할 수 있는 옵션을 정의해요.

**Example: Default**

```tsx
<Menu.Dropdown header={<Menu.Header>편집</Menu.Header>}>
  <Menu.DropdownItem>첫 번째 메뉴</Menu.DropdownItem>
  <Menu.DropdownItem>두 번째 메뉴</Menu.DropdownItem>
  <Menu.DropdownItem>세 번째 메뉴</Menu.DropdownItem>
</Menu.Dropdown>
```

### 아이콘이 포함된 메뉴 사용하기

아이콘이 포함된 메뉴는 옵션의 의미를 시각적으로 강조할 때 유용해요. 예를 들어, 설정 항목이나 상태를 시각적으로 구분해야 할 때 사용해요.
`Menu.DropdownItem`의 `right` 속성에 `Menu.DropdownIcon`을 전달해서 각 항목에 아이콘을 추가할 수 있어요.

**Example: ItemWithIcon**

```tsx
<Menu.Dropdown header={<Menu.Header>편집</Menu.Header>}>
  }>첫 번째 메뉴</Menu.DropdownItem>
  }>두 번째 메뉴</Menu.DropdownItem>
  }>세 번째 메뉴</Menu.DropdownItem>
</Menu.Dropdown>
```

### 체크박스 메뉴 추가하기

`Menu.DropdownCheckItem` 컴포넌트를 사용하면 체크박스를 포함한 메뉴를 만들 수 있어요. `checked`와 `onCheckedChange` 속성을 사용해서 각 항목의 상태를 제어할 수 있어요.

**Example: CheckedItem**

```tsx
<Menu.Dropdown header={<Menu.Header>편집</Menu.Header>}>
  <Menu.DropdownCheckItem checked={false}>첫 번째 메뉴</Menu.DropdownCheckItem>
  <Menu.DropdownCheckItem checked={true}>두 번째 메뉴</Menu.DropdownCheckItem>
  <Menu.DropdownCheckItem checked={false}>세 번째 메뉴</Menu.DropdownCheckItem>
</Menu.Dropdown>
```

### 트리거로 메뉴 열기

`Menu.Trigger` 컴포넌트는 사용자 동작에 따라 메뉴를 열고 닫고 싶을 때 사용해요. `open` 속성을 동적으로 제어해서 버튼 클릭이나 사용자 입력에 따라 상태를 변경할 수 있어요.
예를 들어, "옵션" 버튼을 눌렀을 때 드롭다운 메뉴를 보여주고, 외부를 클릭했을 때 닫히는 동작을 구현할 수 있어요.

`placement` 속성을 사용해서 메뉴가 열리는 위치를 설정할 수 있어요. `placement` 속성의 값은 메뉴가 열릴 방향과 정렬 방식을 결정해요.

- 방향 설정: `top`, `bottom`, `left`, `right`를 사용하여 메뉴가 기준 컴포넌트의 상하좌우 중 어느 방향에 열릴지 결정해요.
- 정렬 설정: `start`와 `end`를 사용하여 메뉴의 시작과 끝을 기준 컴포넌트의 왼쪽 또는 오른쪽에 맞출 수 있어요. 정렬을 지정하지 않으면 중앙에 정렬돼요.

사용 가능한 `placement` 값은 방향과 정렬 조합으로 구성돼요.

- `top`, `top-start`, `top-end`: 메뉴가 상단에 열려요.
- `bottom`, `bottom-start`, `bottom-end`: 메뉴가 하단에 열려요.
- `left`, `left-start`, `left-end`: 메뉴가 왼쪽에 열려요.
- `right`, `right-start`, `right-end`: 메뉴가 오른쪽에 열려요.

**Example: Trigger**

```tsx
function Trigger() {
  const [open, setOpen] = React.useState(false);
  const [checked, setChecked] = React.useState(1);
  return (
    <Menu.Trigger
      open={open}
      onOpen={() => setOpen(true)}
      onClose={() => setOpen(false)}
      placement="bottom"
      dropdown={
        <Menu.Dropdown header={<Menu.Header>항목을 선택하세요</Menu.Header>}>
          <Menu.DropdownCheckItem
            checked={checked === 1}
            onCheckedChange={(checked: boolean) =>
              checked ? setChecked(1) : null
            }
          >
            첫 번째 메뉴
          </Menu.DropdownCheckItem>
          <Menu.DropdownCheckItem
            checked={checked === 2}
            onCheckedChange={(checked: boolean) =>
              checked ? setChecked(2) : null
            }
          >
            두 번째 메뉴
          </Menu.DropdownCheckItem>
          <Menu.DropdownCheckItem
            checked={checked === 3}
            onCheckedChange={(checked: boolean) =>
              checked ? setChecked(3) : null
            }
          >
            세 번째 메뉴
          </Menu.DropdownCheckItem>
        </Menu.Dropdown>
      }
    >
      <Button>클릭해보세요</Button>
    </Menu.Trigger>
  );
}
```

## 인터페이스

**Type: MenuDropdownProps**

```typescript
export interface MenuDropdownProps {
  /**
   * 드롭다운의 헤더를 정의하는 속성이에요.
   * 주로 `Menu.Header` 컴포넌트와 함께 사용해요.
   */
  header?: React.ReactNode;
}
```

**Type: MenuDropdownItemProps**

```typescript
export interface MenuDropdownItemProps {
  /**
   * 드롭다운 아이템 왼쪽에 표시할 컴포넌트예요.
   * 체크박스를 표시하려면 `Menu.DropdownCheckItem` 컴포넌트를 사용하는 것이 좋아요.
   */
  left?: React.ReactNode;
  /**
   * 드롭다운 아이템 오른쪽에 표시할 컴포넌트예요.
   * 아이콘을 표시하려면 `Menu.DropdownIcon` 컴포넌트를 사용하는 것이 좋아요.
   */
  right?: React.ReactNode;
  /**
   * 메뉴 아이템에 들어가는 컴포넌트예요.
   */
  children?: React.ReactNode;
}
```

**Type: MenuDropdownCheckedItemProps**

```typescript
export interface MenuDropdownCheckedItemProps {
  /**
   * 체크박스의 상태를 나타내요.
   */
  checked?: boolean;
  /**
   * 체크 상태가 변경될 때 호출되는 함수예요.
   */
  onCheckedChange?: (checked: boolean) => void;
}
```

**Type: MenuTriggerProps**

```typescript
export interface MenuTriggerProps {
  /**
   * 메뉴의 열림을 제어하는 상태예요.
   * 이 속성을 사용하려면 `onOpen`과 `onClose`도 함께 전달해서 제어 컴포넌트로 설정해야 해요.
   */
  open?: boolean;
  /**
   * 초기 열림 상태예요.
   */
  defaultOpen?: boolean;
  /**
   * 메뉴를 제어하는 트리거 컴포넌트를 정의할 수 있어요.
   */
  children?: React.ReactNode;
  /**
   * `open` 되었을 때 보여지게 될 컴포넌트예요.
   * `Menu.Dropdown` 컴포넌트를 활용해주세요.
   */
  dropdown?: React.ReactNode;
  /**
   * Trigger를 기준으로 메뉴가 열리는 위치를 정할 수 있어요.
   * @default 'bottom-start'
   */
  placement?:
    | "top"
    | "right"
    | "bottom"
    | "left"
    | "left-end"
    | "left-start"
    | "right-end"
    | "right-start"
    | "bottom-end"
    | "bottom-start"
    | "top-end"
    | "top-start";
  /**
   * 메뉴가 열릴 때 호출되는 함수예요.
   * 전달하지 않을 경우, uncontrolled component로 동작해요.
   */
  onOpen?: () => void;
  /**
   * 메뉴가 닫힐 때 호출되는 함수예요.
   * 전달하지 않을 경우, uncontrolled component로 동작해요.
   */
  onClose?: () => void;
}
```

---

# Modal (/tds-mobile/components/modal/)

# Modal

`Modal` 컴포넌트는 사용자의 주의가 필요한 중요한 내용을 표시하거나 즉각적인 상호작용이 필요할 때 사용해요. 화면의 다른 콘텐츠 위에 나타나 사용자의 집중을 유도해요. 사용자가 제공되는 정보를 확인하거나 필요한 동작을 완료해야만 기존 화면으로 돌아갈 수 있어요.

[Preview: Basic]

## 사용 예제

`Modal` 컴포넌트는 `Modal.Overlay`와 `Modal.Content` 두 개의 하위 컴포넌트로 구성되어 있어요. `Modal`에 담길 콘텐츠는 `Modal.Content` 안에 있고, `Modal.Overlay`는 `Modal` 컴포넌트 뒤에 보이는 배경으로 사용자가 콘텐츠에 담긴 내용에 집중하는 것을 도와줘요.

### 기본 사용법

가장 기본적인 `Modal` 컴포넌트의 사용 방법이에요. 버튼을 클릭하면 `Modal` 컴포넌트가 열리고, 확인 버튼이나 오버레이를 클릭하면 `Modal` 컴포넌트가 닫혀요.

**Example: Basic**

```tsx
/** 기본 `Modal` 컴포넌트이에요. */
function Basic() {
  const [open, setOpen] = React.useState<boolean>(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>모달 열기</Button>
      <Modal open={open} onOpenChange={setOpen}>
        <Modal.Content
          style={{
            padding: "32px 20px 20px 20px",
            display: "flex",
            flexDirection: "column",
            alignItems: "center",
            textAlign: "center",
          }}
        >
          <p style={{ marginBottom: "24px" }}>
            동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세
            무궁화 삼천리 화려강산 대한사람 대한으로 길이 보전하세 동해물과
            백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세 무궁화 삼천리
            화려강산 대한사람 대한으로 길이 보전하세
          </p>
          <Button
            display="block"
            color="primary"
            onClick={() => setOpen(false)}
          >
            확인
          </Button>
        </Modal.Content>
      </Modal>
    </>
  );
}
```

### 닫힘 이벤트 처리하기

`Modal` 컴포넌트가 완전히 닫힌 후 특정 동작을 수행하고 싶다면 `onExited` 콜백을 사용하세요. 이 콜백은 `Modal` 컴포넌트가 완전히 닫히고 애니메이션이 완료된 후에 호출되기 때문에 리소스 해제나 후속 작업을 처리하기에 적합해요.

**Example: OnExitModal**

```tsx
/** onExit 콜백 활용한 `Modal` 컴포넌트이에요. */
function OnExitModal() {
  const [open, setOpen] = React.useState<boolean>(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>모달 열기</Button>
      <Modal
        open={open}
        onOpenChange={setOpen}
        onExited={() => alert("모달이 완전히 닫혔어요.")}
      >
        <Modal.Content
          style={{
            padding: "32px 20px 20px 20px",
            display: "flex",
            flexDirection: "column",
            alignItems: "center",
            textAlign: "center",
          }}
        >
          <p style={{ marginBottom: "24px" }}>
            동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세
            무궁화 삼천리 화려강산 대한사람 대한으로 길이 보전하세 동해물과
            백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세 무궁화 삼천리
            화려강산 대한사람 대한으로 길이 보전하세
          </p>
          <Button
            display="block"
            color="primary"
            onClick={() => setOpen(false)}
          >
            확인
          </Button>
        </Modal.Content>
      </Modal>
    </>
  );
}
```

### 오버레이 클릭 이벤트 처리하기

`Modal` 컴포넌트의 오버레이(배경) 클릭 시 특별한 동작을 수행하고 싶다면 `Modal.Overlay`의 `onClick` 콜백을 사용하세요. 예를 들어, 배경을 클릭하면 `Modal` 컴포넌트를 닫거나 추가 작업을 실행할 수 있어요.

일반적인 사용 예시를 참고해 보세요.

- 입력 폼의 내용이 있을 때 "저장하지 않고 나가시겠습니까?" 확인하기
- 결제 진행 중에 실수로 닫는 것을 방지하기 위한 한 번 더 확인하기
- `Modal` 컴포넌트가 닫힐 때 입력 내용 초기화하기

**Example: OverlayCallbackModal**

```tsx
/** 오버레이의 onClick 콜백을 활용하는 `Modal` 컴포넌트이에요. */
function OverlayCallbackModal() {
  const [open, setOpen] = React.useState<boolean>(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>모달 열기</Button>
      <Modal
        open={open}
        onOpenChange={setOpen}
        onExited={() => alert("모달이 닫혔습니다")}
      >
        <Modal.Overlay onClick={() => alert("오버레이를 클릭했어요.")} />
        <Modal.Content
          style={{
            padding: "32px 20px 20px 20px",
            display: "flex",
            flexDirection: "column",
            alignItems: "center",
            textAlign: "center",
          }}
        >
          <p style={{ marginBottom: "24px" }}>
            동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세
            무궁화 삼천리 화려강산 대한사람 대한으로 길이 보전하세 동해물과
            백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세 무궁화 삼천리
            화려강산 대한사람 대한으로 길이 보전하세
          </p>
        </Modal.Content>
      </Modal>
    </>
  );
}
```

## 접근성

- `Modal` 컴포넌트는 다음과 같은 접근성 기능을 제공해요.

### 기본 접근성 지원

다음 속성이 있어서 다른 설정 없이도 기본적으로 사용자의 접근성을 고려한 `Modal` 컴포넌트를 제공할 수 있어요.

| 속성            | 접근성 효과                                                | 설명                                                                                       |
| --------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| `aria-hidden`   | `Modal` 컴포넌트의 외부 콘텐츠가 스크린 리더에서 숨겨져요. | `Modal` 컴포넌트가 열린 동안 배경 콘텐츠는 스크린 리더가 읽지 않아요.                      |
| `tabIndex={0}`  | `Modal` 컴포넌트의 내부로 키보드 포커스가 이동해요.        | `Modal` 컴포넌트가 열리면 자동으로 포커스를 받을 수 있어요.                                |
| `role="button"` | 오버레이가 클릭 가능한 요소임을 알려줘요.                  | 스크린 리더 사용자가 오버레이 클릭으로 `Modal` 컴포넌트를 닫을 수 있음을 인지할 수 있어요. |

## 인터페이스

**Type: ModalProps**

```typescript
export interface ModalProps {
  /**
   * `Modal` 컴포넌트의 열림/닫힘 상태를 제어해요.
   *
   * 이 값이 `true`라면 `Modal` 컴포넌트가 열려요.
   *
   * 이 값이 `false`라면 `Modal` 컴포넌트가 닫혀있어요.
   */
  open?: boolean;

  /**
   * `Modal` 컴포넌트의 상태가 변경될 때 호출되는 콜백이에요.
   * `Modal` 컴포넌트가 열리거나 닫힐 때 실행돼요.
   */
  onOpenChange?: (open: boolean) => void;

  /**
   * `Modal` 컴포넌트가 닫히고 애니메이션이 완료된 후 호출되는 콜백이에요.
   */
  onExited?: () => void;

  /**
   * `Modal` 컴포넌트가 렌더링될 DOM 요소를 지정해요.
   *
   * `Modal` 컴포넌트는 기본적으로 document.body에 렌더링돼요.
   *
   * @default document.body
   */
  portalContainer?: HTMLElement | null;
}
```

**Type: ModalOverlayProps**

```typescript
export interface ModalOverlayProps {
  /**
   * `Modal` 컴포넌트의 오버레이(배경) 클릭 시 호출되는 콜백이에요.
   */
  onClick?: () => void;
}
```

---

# Numeric Spinner (/tds-mobile/components/numeric-spinner/)

# Numeric Spinner

`NumericSpinner` 컴포넌트는 정수 입력을 쉽게 처리할 수 있도록, 숫자를 증감시키는 버튼을 제공해요. 키보드 없이 숫자를 입력하거나 수정할 때 사용해요.

[Preview: NumericSpinner]

## 사용법

### 입력값 관리

#### 입력값을 외부에서 관리하기

`NumericSpinner` 컴포넌트의 입력값을 외부에서 관리하려면, `number`, `onNumberChange` 속성을 함께 사용하세요. `number`는 컴포넌트에 현재 값을 제공하고, `onNumberChange`는 입력값이 바뀔 때 호출되는 함수예요.

**Example: Controlled**

```tsx
function Controlled() {
  const [value, setValue] = React.useState(0);

  return (
    <NumericSpinner
      size="large"
      number={value}
      onNumberChange={(number) => {
        setValue(number);
      }}
    />
  );
}
```

#### 입력값을 내부에서 관리하기

`NumericSpinner` 컴포넌트의 입력값을 내부에서 관리하려면, `defaultNumber` 속성에 값을 설정하세요. 설정한 값이 초기 입력값이 되고 이후 입력값의 변경은 `NumericSpinner` 컴포넌트 내부에서 처리돼요. 이 방식은 외부에서 값을 따로 관리할 필요가 없을 때 적합해요.

**Example: Uncontrolled**

```tsx

```

### 크기 변경하기

`NumericSpinner` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. 지원되는 크기는 `small`, `medium`, `large`가 있어요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}></div>
```

### 비활성화하기

`NumericSpinner` 컴포넌트를 비활성화하려면 `disable` 속성을 사용하세요. 비활성화된 `NumericSpinner` 컴포넌트는 버튼을 클릭해도 숫자가 변하지 않아요.

**Example: Disable**

```tsx

```

## 접근성

`NumericSpinner` 컴포넌트는 기본적으로 접근성을 지원하는 여러 속성을 포함하고 있어요. 이 속성들은 스크린 리더 사용자들이 컴포넌트를 명확하게 이해하고 상호작용할 수 있도록 도와줘요.

| 속성                 | 접근성 효과                                                 | 설명                                                         |
| -------------------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| `<button>` 태그      | 스크린 리더가 버튼으로 인식해요.                            | 사용자는 해당 요소가 상호작용 가능한 버튼임을 알 수 있어요.  |
| `aria-live="polite"` | 수량 변경 시 변경된 숫자를 스크린 리더가 자동으로 읽어줘요. | 사용자는 실시간으로 업데이트되는 수량 정보를 들을 수 있어요. |
| `decreaseAriaLabel`  | 감소 버튼의 기능을 설명해요.                                | 스크린 리더 사용자에게 버튼의 목적을 명확히 전달해요.        |
| `increaseAriaLabel`  | 증가 버튼의 기능을 설명해요.                                | 스크린 리더 사용자에게 버튼의 목적을 명확히 전달해요.        |

### 추가로 지원해야 하는 접근성

기본적인 접근성 제공 외에도, `decreaseAriaLabel`과 `increaseAriaLabel` props를 사용해서 더 구체적인 상황에서 사용자 경험을 개선할 수 있어요. 예를 들면 이 props들은 기본값으로 "빼기", "더하기"로 설정되어 있지만, 상황에 따라 의미가 달라지면 반드시 변경해야 해요.
예를 들어 상품 수량과 관련된 UI에서 사용될 때, 다음과 같이 라벨의 값을 바꿔서 버튼의 기능을 더 명확하게 설명할 수 있어요.

```jsx
<NumericSpinner
  number={value}
  onNumberChange={setValue}
  decreaseAriaLabel="상품 수량 줄이기"
  increaseAriaLabel="상품 수량 늘리기"
/>
```

이렇게 적절한 `aria-label`을 제공하면, 스크린 리더 사용자들이 버튼의 목적을 정확히 이해하고 사용할 수 있어요. 상황에 맞게 명확한 레이블을 제공하는 것이 접근성 향상에 매우 중요해요.

## 인터페이스

**Type: NumericSpinnerProps**

```typescript
export interface NumericSpinnerProps {
  /**
   * `NumericSpinner` 컴포넌트의 크기에요
   */
  size: "tiny" | "small" | "medium" | "large";
  /**
   * `NumericSpinner` 컴포넌트에 표시되는 값이에요. 주로 입력값을 컴포넌트 외부에서 관리할 때 `onNumberChange` 속성과 함께 사용해요.
   *
   * @default 0
   */
  number?: number;
  /**
   * `NumericSpinner` 컴포넌트의 초기 입력값이에요. 설정된 값으로 컴포넌트가 초기화되고, 이후 입력값은 `NumericSpinner` 컴포넌트 내부에서 관리돼요. 외부에서 값 변경을 추적할 필요가 없을 때 사용해요.
   */
  defaultNumber?: number;
  /**
   * 입력할 수 있는 최소값이에요. 설정된 값보다 작은 값은 사용자가 입력할 수 없어요.
   *
   * @default 0
   */
  minNumber?: number;
  /**
   * 입력할 수 있는 최대값이에요. 설정된 값보다 큰 값은 사용자가 입력할 수 없어요.
   *
   * @default 999
   */
  maxNumber?: number;
  /**
   * 이 값이 true일 때 `NumericSpinner` 컴포넌트가 비활성화돼요. 사용자가 버튼을 눌러도 숫자가 변하지 않아요.
   *
   * @default false
   */
  disable?: boolean;
  /**
   * 입력값이 변경될 때 호출되는 함수예요. 변경된 숫자 값을 매개변수로 받아 처리해요.
   * 예를 들어, 입력값이 변경되면 이를 외부 상태에 반영할 때 사용해요.
   */
  onNumberChange?: (number: number) => void;
}
```

---

# Paragraph (/tds-mobile/components/paragraph/)

# Paragraph

`Paragraph` 컴포넌트는 텍스트를 표시하는 데 사용돼요.

다양한 하위 요소나 속성을 조합해서 더 복잡한 구성을 할 수 있도록 설계되었어요.  
이 문서에서는 `Paragraph`의 각 하위 요소가 어떤 역할을 하는지, 그리고 다양한 요소를 조합해 컴포넌트를 어떻게 사용하는지 쉽게 이해할 수 있어요.

[Preview: Paragraph]

## 사용법

### 텍스트 표현하기

`Paragraph.Text`를 활용해서 텍스트를 표현할 수 있어요.  
`Paragraph.Text`에서 사용할 수 있는 속성들은 [ParagraphTextProps](#paragraphtext)를 참고해 주세요.

**Example: WithText**

```tsx
<Paragraph typography="t5">
  <Paragraph.Text>동해물과 백두산이 마르고 닳도록</Paragraph.Text>
  <Paragraph.Text>하느님이 보우하사</Paragraph.Text>
  <Paragraph.Text>우리나라 만세</Paragraph.Text>
</Paragraph>
```

### 아이콘 그리기

아이콘을 그리려면 `Paragraph.Icon` 컴포넌트를 사용하세요.  
`Paragraph.Icon`에서 사용할 수 있는 속성들은 [ParagraphIconProps](#paragraphicon)를 참고해 주세요.

**Example: WithIcon**

```tsx
<Paragraph typography="t5">
  <Paragraph.Text>{`동해물과 백두산이\n마르고 닳도록`}</Paragraph.Text>

  <Paragraph.Text>하느님이 보우하사</Paragraph.Text>
</Paragraph>
```

### 뱃지 그리기

뱃지를 그리려면 `Paragraph.Badge` 컴포넌트를 사용하세요.  
`Paragraph.Badge`에서 사용할 수 있는 속성들은 [ParagraphBadgeProps](#paragraphbadge)를 참고해 주세요.

**Example: WithBadge**

```tsx
<Paragraph typography="t5">
  <Paragraph.Text>{`동해물과 백두산이\n마르고 닳도록`}</Paragraph.Text>
  <Paragraph.Text>하느님이 보우하사</Paragraph.Text>
  <Paragraph.Badge color="blue" variant="fill">
    우리
  </Paragraph.Badge>
  <Paragraph.Badge color="red" variant="weak">
    나라
  </Paragraph.Badge>
  <Paragraph.Badge color="teal" variant="fill">
    만세
  </Paragraph.Badge>
</Paragraph>
```

### 링크 그리기

링크를 그리려면 `Paragraph.Link` 컴포넌트를 사용하세요.  
`Paragraph.Link`에서 사용할 수 있는 속성들은 [ParagraphLinkProps](#paragraphlink)를 참고해 주세요.

`type` 속성을 통해 두 가지 스타일을 적용할 수 있어요.

- `underline`: 밑줄이 있는 링크
- `none`: 밑줄이 없는 링크

**Example: WithLink**

```tsx
<Paragraph typography="t5">
  <Paragraph.Text>일반 텍스트 사이에 </Paragraph.Text>

  <Paragraph.Link
    as="a"
    href="https://toss.im"
    type="underline"
    color={adaptive.green600}
  >
    <Paragraph.Text>밑줄이 있는 링크</Paragraph.Text>
  </Paragraph.Link>

  <Paragraph.Text>를 넣을 수 있어요. </Paragraph.Text>

  <Paragraph.Link as="a" href="https://toss.im">
    밑줄이 없는 링크는 기본 색상이 blue500이에요.
  </Paragraph.Link>

  <Paragraph.Link as="a" href="https://toss.im" type="underline">
    <Paragraph.Text>이미지, </Paragraph.Text>{" "}
    <Paragraph.Badge color="red" variant="weak">
      뱃지
    </Paragraph.Badge>
    <Paragraph.Text>컴포넌트를 내부에 넣을 수 있어요.</Paragraph.Text>
  </Paragraph.Link>
</Paragraph>
```

## 인터페이스

### Paragraph

### ParagraphText

### ParagraphBadge

### ParagraphLink

### ParagraphIcon

---

# Post (/tds-mobile/components/post/)

# Post

`Post` 컴포넌트는 포스트 형식의 줄글을 쓸 때 적용되는 스타일이에요. 각 스타일은 제목, 본문, 목록과 같은 구성요소로 나뉘어 있으며, 정보를 효과적으로 시각화해요. 공지 사항이나 이벤트 페이지 등에 사용해요.

[Preview: Basic]

## 사용법

### 제목에서 사용하기

제목 스타일은 중요도에 따라 다양한 크기로 구분해요. 제목에서 사용할 수 있는 컴포넌트는 4가지 종류가 있어요.

- `Post.H1`: 가장 큰 제목에 사용해요.
- `Post.H2`: 큰 제목에 사용해요.
- `Post.H3`: 일반적인 제목에 사용해요.
- `Post.H4`: 작은 제목에 사용해요.

**Example: Heading**

```tsx
<div>
  <Post.H1>H1 제목 타이틀</Post.H1>
  <Post.H2>H2 제목 타이틀</Post.H2>
  <Post.H3>H3 제목 타이틀</Post.H3>
  <Post.H4>H4 제목 타이틀</Post.H4>
</div>
```

### 본문에서 사용하기

`Post.Paragraph` 컴포넌트는 기본 본문 스타일로, 주로 설명이 필요한 텍스트에 사용해요. 긴 문장을 잘 읽히도록 가독성 높은 글꼴과 적절한 여백을 제공해요.

**Example: Paragraph**

```tsx
<div>
  <Post.Paragraph>
    2018년 11월 22일부터 토스 가입 시 자동 발급되는 토스 계좌의 명칭이 {"'"}
    토스머니{"'"}로 변경됩니다.
    <br />
    <br />
    또한, 토스 제휴 금융사 계좌 개설 시 자동 삭제되었던 토스머니가 다시
    생성되며, 앞으로 모든 연락처 송금은 토스머니로 입금됩니다.
  </Post.Paragraph>
  <Post.Paragraph typography="t7">
    2018년 11월 22일부터 토스 가입 시 자동 발급되는 토스 계좌의 명칭이 {"'"}
    토스머니{"'"}로 변경됩니다.
    <br />
    <br />
    또한, 토스 제휴 금융사 계좌 개설 시 자동 삭제되었던 토스머니가 다시
    생성되며, 앞으로 모든 연락처 송금은 토스머니로 입금됩니다.
  </Post.Paragraph>
</div>
```

### 목록에서 사용하기

관련된 정보를 항목별로 구분하여 사용자에게 이해하기 쉽게 제공해요. 목록 스타일은 순서가 필요한 경우와 그렇지 않은 경우로 나뉘어 있어요.
순서가 필요한 경우에는 `Post.Ol` 컴포넌트를 사용해요. 그렇지 않은 경우에는 `Post.Ul` 컴포넌트를 사용해요.

각 항목을 표시할 경우에는 `Post.Li` 컴포넌트를 사용해요. `Post.Li` 컴포넌트는 부모 요소인 `Post.Ol`, `Post.Ul`에 포함하여 사용해요.

#### 순서가 필요할 때

`Post.Ol` 컴포넌트는 순서가 필요한 항목을 번호로 표시해요. 주로 단계별 지시 사항이나 절차를 안내하는데 적합해요.

**Example: OrderedList**

```tsx
<Post.Ol>
  <Post.Li>
    2018년 11월 22일부터 토스 가입 시 자동 발급되는 토스 계좌의 명칭이 {"'"}
    토스머니{"'"}로 변경됩니다.
  </Post.Li>
  <Post.Li>
    리스트 텍스트
    <Post.Ol>
      <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
      <Post.Li>
        리스트 안의 리스트 텍스트
        <Post.Ol>
          <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
          <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
        </Post.Ol>
      </Post.Li>
    </Post.Ol>
  </Post.Li>
  <Post.Li>
    리스트 텍스트
    <Post.Ol>
      <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
    </Post.Ol>
  </Post.Li>
</Post.Ol>
```

#### 순서가 필요하지 않을 때

`Post.Ul` 컴포넌트는 순서가 필요하지 않은 항목을 불릿 형태로 표시해요. 주로 간단한 정보나 조건 목록 등에 적합해요.

**Example: UnorderedList**

```tsx
<Post.Ul>
  <Post.Li>
    2018년 11월 22일부터 토스 가입 시 자동 발급되는 토스 계좌의 명칭이 {"'"}
    토스머니{"'"}로 변경됩니다.
  </Post.Li>
  <Post.Li>
    리스트 텍스트
    <Post.Ul>
      <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
      <Post.Li>
        리스트 안의 리스트 텍스트
        <Post.Ul>
          <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
          <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
        </Post.Ul>
      </Post.Li>
    </Post.Ul>
  </Post.Li>
  <Post.Li>
    리스트 텍스트
    <Post.Ul>
      <Post.Li>리스트 안의 리스트 텍스트</Post.Li>
    </Post.Ul>
  </Post.Li>
</Post.Ul>
```

### 구분선 사용하기

`Post.Hr` 컴포넌트는 요소 주위에 선을 그려서 요소 간의 구분을 명확히 하고 싶을 때 사용해요. UI 요소 간의 명확한 구분과 계층 구조를 표현할 수 있어요.

**Example: Hr**

```tsx
<div>
  <Post.Paragraph>
    2018년 11월 22일부터 토스 가입 시 자동 발급되는 토스 계좌의 명칭이 {"'"}
    토스머니{"'"}로 변경됩니다.
  </Post.Paragraph>

  <Post.Paragraph>
    2018년 11월 22일부터 토스 가입 시 자동 발급되는 토스 계좌의 명칭이 {"'"}
    토스머니{"'"}로 변경됩니다.
  </Post.Paragraph>
</div>
```

## 인터페이스

**Type: PostH1Props**

```typescript
export interface PostH1Props {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   * @default "t2"
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostH2Props**

```typescript
export interface PostH2Props {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   * @default "t3"
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostH3Props**

```typescript
export interface PostH3Props {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   * @default "st8"
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostH4Props**

```typescript
export interface PostH4Props {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   * @default "t5"
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostParagraphProps**

```typescript
export interface PostParagraphProps {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostOlProps**

```typescript
export interface PostOlProps {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostUlProps**

```typescript
export interface PostUlProps {
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 각 스타일은 텍스트의 크기, 굵기, 간격 등을 다르게 설정해서 다양한 화면 환경과 디자인 요구를 만족해요.
   *
   * `t1` ~ `t7`: 주로 본문 텍스트에 사용하는 크기와 굵기 스타일이에요.
   * `st1` ~ `st13`: 서브 타이틀 또는 부가적인 텍스트에 적합한 스타일이에요. 예를 들어, `st1`은 작은 본문이나 설명 텍스트에 적합하고, `st10`은 강조 텍스트에 사용하기 좋아요.
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

**Type: PostHrProps**

```typescript
export interface PostHrProps {
  /**
   * 구분선의 아래 여백 크기를 결정해요. 단위는 `px`이에요. 예를 들어, `paddingBottom={10}`으로 설정하면 강조 영역 내부에 10px의 여백이 생겨요.
   */
  paddingBottom?: number | string;
}
```

---

# ProgressBar (/tds-mobile/components/progress-bar/)

# ProgressBar

`ProgressBar` 컴포넌트는 작업의 진행 상태를 시각적으로 표시하는 데 사용해요. 데이터 로딩, 단계별 진행 상황 등 다양한 작업의 완료 정도를 사용자에게 직관적으로 보여줄 수 있어요.

[Preview: Basic]

## 사용법

### 진행도 표시하기

`progress` 속성에 0.0부터 1.0 사이의 값을 전달하여 진행도를 표시할 수 있어요.

**Example: Basic**

```tsx

```

### 크기 지정하기

`size` 속성을 통해 `ProgressBar` 컴포넌트의 크기를 지정할 수 있어요.
세 가지 크기(`light`, `normal`, `bold`)를 제공하며, 기본값은 `normal`이에요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", flexDirection: "column", gap: 16 }}></div>
```

### 색상 변경하기

`color` 속성을 사용하여 진행 바의 색상을 변경할 수 있어요.
CSS 색상 값을 지정할 수 있으며, 기본값은 `blue400` 색상이에요.

**Example: Colors**

```tsx
<div style={{ display: "flex", flexDirection: "column", gap: 16 }}></div>
```

### 애니메이션 효과 추가하기

`animate` 속성을 `true`로 설정하면, 진행도가 변경될 때 부드러운 애니메이션 효과가 적용돼요.

**Example: Animated**

```tsx
function Animated() {
  const [progress, setProgress] = React.useState<number>(0);

  const handleClick = () => {
    setProgress(progress === 0 ? 1 : 0);
  };

  return (
    <div style={{ display: "flex", flexDirection: "column", gap: 40 }}>
      <Button onClick={handleClick} size="medium">
        {progress === 0 ? "애니메이션 시작" : "애니메이션 리셋"}
      </Button>
    </div>
  );
}
```

## 인터페이스

**Type: ProgressBarProps**

```typescript
export interface ProgressBarProps {
  /**
   * `ProgressBar` 컴포넌트의 진행도를 나타내요.
   *
   * 0.0부터 1.0 사이의 값을 가질 수 있어요.
   *
   * 예를 들어, 0.5는 50% 진행을 의미해요.
   */
  progress: number;

  /**
   * `ProgressBar` 컴포넌트의 크기를 결정해요.
   *
   * `light`, `normal`, `bold` 세 가지 크기를 제공해요.
   *
   * @default 'normal'
   */
  size: "light" | "normal" | "bold";

  /**
   * `ProgressBar` 컴포넌트의 색상을 결정해요.
   *
   * @default colors.blue400
   */
  color?: string;

  /**
   * 애니메이션을 적용할지 여부를 결정해요.
   *
   * @default false
   */
  animate?: boolean;

  /**
   * `ProgressBar` 컴포넌트의 `className`을 지정해요.
   */
  className?: string;
}
```

---

# ProgressStepper (/tds-mobile/components/progress-stepper/)

# ProgressStepper

`ProgressStepper` 컴포넌트는 프로그레스바와 스테퍼가 결합된 형태로, 작업의 진행 상태를 단계별로 시각적으로 표시하는 데 사용해요.
각 단계의 제목을 설정하면 사용자에게 현재 진행 중인 단계와 앞으로의 단계를 명확하게 보여줄 수 있어요.
단계별 진행 상황을 한눈에 확인할 수 있어, 작업의 완료 정도를 효과적으로 표현할 수 있어요.

[Preview: Basic]

## 사용법

### 형태 변경하기

`variant` 속성을 사용하면 `ProgressStepper` 컴포넌트의 스타일을 변경할 수 있어요. 사용 가능한 형태는 `compact`, `icon`가 있어요.

- `compact`: 단계가 간결하게 표시되는 스타일로, 명확한 진행 상태를 보여줘요.
- `icon`: 각 단계에 아이콘이 추가되어 쉽게 알아볼 수 있고, 시각적으로 더 직관적인 단계 구분이 가능해요.

**Example: Variant**

```tsx
<div>
  <ProgressStepper variant="compact" activeStepIndex={1}></ProgressStepper>
  <ProgressStepper
    variant="icon"
    activeStepIndex={1}
    paddingTop="wide"
  ></ProgressStepper>
</div>
```

### 단순한 형태로 사용하기

`ProgressStep` 컴포넌트의 `title` 속성을 생략하면 단순한 형태의 스텝퍼를 사용할 수 있어요. 이 형태는 단계의 진행 상태만을 간단히 표시하고 싶을 때 유용해요.
특히 제한된 공간에서 진행 상태를 표시하거나, 단계별 설명이 불필요할 때 사용해요.

**Example: VariantWithoutTitle**

```tsx
<div>
  <ProgressStepper variant="compact" activeStepIndex={1}></ProgressStepper>
  <ProgressStepper
    variant="icon"
    activeStepIndex={1}
    paddingTop="wide"
  ></ProgressStepper>
</div>
```

### 완료된 단계 표시하기

`ProgressStepper` 컴포넌트의 `variant` 속성을 `icon`으로 설정하고 `checkForFinish` 속성을 `true`로 설정하면, 현재 단계 이전의 모든 단계가 체크 아이콘으로 표시돼요.
이렇게 하면 어떤 단계를 다 끝냈는지 바로 알 수 있어요.

**Example: IconWithActiveStepIndex**

```tsx
<ProgressStepper
  variant="icon"
  activeStepIndex={2}
  checkForFinish
></ProgressStepper>
```

### 단계별 아이콘 설정하기

`ProgressStepper` 컴포넌트의 `variant` 속성을 `icon`으로 설정하면 각 단계에 아이콘을 추가할 수 있어요.
`ProgressStep` 컴포넌트의 `icon` 속성을 사용해서 각 단계별로 의미 있는 아이콘을 사용할 수 있어요.
아이콘을 사용하면 각 단계의 특성을 시각적으로 명확하게 구분할 수 있고, 사용자가 진행 상태를 한 눈에 확인하는 데 도움이 돼요.

**Example: IconWithResourceStep**

```tsx
<ProgressStepper variant="icon" activeStepIndex={1}>
  }
  />
  }
  />
  }
  />
</ProgressStepper>
```

## 인터페이스

**Type: ProgressStepperProps**

```typescript
export interface ProgressStepperProps {
  /**
   * 진행 단계를 표시하는 스타일을 설정해요.
   *
   * - compact: 간결한 스타일
   * - icon: 아이콘이 포함된 스타일
   */
  variant: "compact" | "icon";
  /**
   * 상단 여백을 조절해요.
   *
   * - wide: 24px
   * - default: 16px
   * @default 'default'
   */
  paddingTop?: "default" | "wide";
  /**
   * 현재 진행 단계를 설정할 수 있어요.
   * @default 0
   */
  activeStepIndex?: number;
  /**
   * `variant` 속성이 `icon`일 때만 사용할 수 있어요.
   * `activeStepIndex` 보다 낮은 단계의 `ProgressStep`을 check icon으로 렌더링해요.
   * @default false
   */
  checkForFinish?: boolean;
}
```

**Type: ProgressStepProps**

```typescript
export interface ProgressStepProps {
  /**
   * 각 단계의 제목을 설정해요.
   */
  title?: string;
  /**
   * `ProgressStepper` 컴포넌트의 `variant` 속성이 `icon`일 때만 사용할 수 있어요.
   * 각 단계별 사용할 아이콘을 렌더링해요.
   */
  icon?: React.ReactNode;
}
```

---

# Rating (/tds-mobile/components/rating/)

# Rating

`Rating` 컴포넌트는 사용자가 주어진 항목이나 콘텐츠에 대한 평가를 제공할 수 있도록 해주는 UI 요소예요. 사용자는 아이콘 개수를 선택해 자신의 만족도를 표현할 수 있고, 선택된 점수에 따라 시각적으로도 즉각 반영돼요. 이 컴포넌트는 상호작용 방식에 따라 읽기 전용 또는 상호작용 가능한 형태로 제공될 수 있어요.

[Preview: Rating]

## 사용 예제

### 크기 조정하기

`Rating` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. `medium`, `large`, `big` 중 하나를 선택할 수 있어요.

**Example: SizeRatings**

```tsx
function SizeRatings() {
  const [valueMedium, setValueMedium] = React.useState<number>(5);
  const [valueLarge, setValueLarge] = React.useState<number>(5);
  const [valueBig, setValueBig] = React.useState<number>(5);

  return (
    <div style={{ display: "flex", gap: "32px", alignItems: "center" }}></div>
  );
}
```

### 읽기 전용으로 사용하기

`Rating` 컴포넌트를 읽기 전용으로 사용하려면 `readOnly` 속성을 사용하세요. `readOnly`를 `true`로 설정하면 읽기 전용으로 사용할 수 있어요. 반대로, 상호작용할 수 있는 `Rating` 컴포넌트를 사용하려면 `readOnly`를 `false`로 설정하면 돼요.

#### 형태 변경하기

읽기 전용으로 사용되는 `Rating` 컴포넌트의 형태를 변경하려면 `variant` 속성을 사용하세요. 선택할 수 있는 값에는 `full`, `compact`, `iconOnly`가 있어요.

**Example: ReadOnlyRatings**

```tsx
<div style={{ display: "flex", gap: "32px", alignItems: "center" }}></div>
```

#### 크기 조정하기

읽기 전용으로 사용되는 `Rating` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. 상호작용이 가능한 `Rating` 컴포넌트와는 달리 `tiny`, `small`, `medium`, `large`, `big` 중 하나를 선택할 수 있어요.

**Example: SizeReadOnlyFullRatings**

```tsx
<div style={{ display: "flex", gap: "32px", alignItems: "center" }}></div>
```

### 비활성화하기

`Rating` 컴포넌트를 비활성화하려면 `disabled` 속성을 사용하세요. 비활성화된 `Rating` 컴포넌트는 사용자와 상호작용할 수 없고, 시각적으로도 비활성화된 상태임을 나타내요.

**Example: DisabledRatings**

```tsx
function DisabledRatings() {
  const [value, setValue] = React.useState<number>(5);

  const handleValueChange = (newValue: number) => {
    setValue(newValue);
  };
  return (
    <div style={{ display: "flex", gap: "32px", alignItems: "center" }}></div>
  );
}
```

## 접근성

- `Rating` 컴포넌트는 기본적으로 접근성을 지원하는 여러 속성을 포함하고 있어요. 이 속성들은 스크린 리더 사용자들이 컴포넌트를 명확하게 이해하고 상호작용할 수 있도록 도와줘요.

### 기본 접근성 지원

다음 속성이 있어서 다른 설정 없이도 기본적으로 사용자의 접근성을 고려한 `Rating` 컴포넌트를 제공할 수 있어요.

| 속성                 | 접근성 효과                                                                                          | 설명                                                                                                                               |
| -------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `aria-label`         | 스크린 리더에서 기본적으로 "별점 평가"로 인식해요.                                                   | 요소의 역할을 명확히 전달하여 사용자가 현재 평가 시스템임을 이해하도록 해요.                                                       |
| `aria-valuetext`     | 현재 선택된 평가 값을 스크린 리더에서 알려줘요. 기본적으로 "`max`점 만점 중 `value`점"으로 인식해요. | 점수의 상태에 따라 읽기 쉽게 텍스트로 표현된 만점 중 현재 평가 값 (1점, 2점 등)을 사용자에게 전달해요.                             |
| `aria-hidden={true}` | 불필요한 정보를 스크린 리더가 읽지 않도록 해요.                                                      | 별 아이콘들은 시각적으로 평점을 나타내지만, 해당 상태는 이미 aria-valuetext 속성을 통해 전달되므로 스크린 리더가 읽지 않도록 해요. |

```jsx
<Rating readOnly={false} value={3} max={5} size="medium" variant="full" aria-label="별점평가" aria-valuetext={`5점 만점 중 3점`}/>
<Rating readOnly={true} value={4} max={5} size="medium" variant="full" aria-label="현재 별점 현황" aria-valuetext={`5점 만점 중 4점`} aria-hidden={false}/>
```

`Rating` 컴포넌트에서는 접근성을 위해 화면에 보이지 않는 `<input type="range" />` 요소를 포함하고 있어요.

대신 시각적으로 보이는 요소에 `aria-label`과 `aria-valuetext` 속성이 적용되어 있어, 스크린 리더 사용자에게 올바른 정보를 전달할 수 있어요.

## 인터페이스

**Type: RatingProps**

```typescript
export interface RatingProps {
  /**
   * 읽기 전용으로 할지, 점수를 매길 수 있는 컴포넌트로 활용할지 결정해요.
   */
  readOnly: false | true;
  /**
   * `Rating` 컴포넌트에서 최대 점수를 결정해요.
   * @default 5
   */
  max?: number;
  /**
   * `Rating` 컴포넌트에서 현재 점수를 결정해요.
   */
  value: number;
  /**
   * `Rating` 컴포넌트의 크기를 결정해요.
   *
   * `readOnly` 값이 `false` 일 때는, `size` 속성으로 `medium`, `large`, `big`을 제공하고 있어요.
   *
   * `readOnly` 값이 `true` 일 때는, `size` 속성으로 `tiny`, `small`, `medium`, `large`, `big`을 제공하고 있어요.
   */
  size: "tiny" | "small" | "medium" | "large" | "big";
  /**
   * `Rating` 컴포넌트의 점수 상태가 바뀔 때 실행되는 함수에요. `readOnly` 값이 `true` 일 때는 사용하지 못해요.
   * @default undefined
   */
  onValueChange?: (value: number) => void;
  /**
   * `Rating` 컴포넌트가 읽기 전용일 때, 컴포넌트의 형태 및 스타일을 결정해요. `readOnly` 값이 `false` 일 때는 사용하지 못해요.
   */
  variant: "full" | "compact" | "iconOnly";
  /**
   * 이 값이 `true` 일 때 `Rating` 컴포넌트가 비활성화돼요. `readOnly` 값이 `true` 일 때는 사용하지 못해요.
   * @default false
   */
  disabled?: false | true;
}
```

---

# Result (/tds-mobile/components/result/)

# Result

`Result` 컴포넌트는 특정 작업의 결과를 시각적으로 보여주는 페이지 컴포넌트예요. 주로 사용자가 작업을 성공했을 때나 에러가 발생했을 때 결과를 알리고, 다양한 메시지나 액션을 제공하는 데 사용해요. 이 컴포넌트를 사용하면 텍스트, 버튼, 이미지 같은 요소들을 손쉽게 배치할 수 있어요.

[Preview: Basic]

## 사용법

### 요소 추가하기

`figure` 속성을 사용하면 제목 상단에 다양한 시각적 요소를 추가할 수 있어요. `Asset` 컴포넌트를 활용해 아이콘, 로띠, 이미지 등의 리소스를 손쉽게 표현할 수 있어요. 이렇게 시각적 요소를 활용하면 사용자에게 메시지를 직관적으로 전달할 수 있어요.

**Example: Figures**

```tsx

  }
  title="라이브 쇼핑 준비 중"
  description="요금이 나오면 알림을 보내드릴게요."
/>
```

### 버튼 추가하기

`button` 속성을 사용하면 설명 아래에 액션 버튼을 추가할 수 있어요. `Result.Button` 컴포넌트를 활용해서 다시 시도하기, 홈으로 돌아가기 등의 동작을 쉽게 구현할 수 있어요. 사용자는 이 버튼으로 필요한 액션을 바로 수행할 수 있어요.

**Example: Buttons**

```tsx
}
  title="다시 접속해주세요"
  description={`페이지를 불러올 수 없습니다\n다시 시도해주세요`}
  button={<Result.Button>재시도</Result.Button>}
/>
```

## 접근성

`Result` 컴포넌트는 기본적으로 접근성을 지원하기 위해 여러 속성을 포함하고 있어요. 이러한 속성을 사용하면 스크린 리더 사용자들이 에러 메시지 확인 및 추가 액션을 쉽게 수행할 수 있어요.

| 속성       | 접근성 효과                             | 설명                                                                                          |
| ---------- | --------------------------------------- | --------------------------------------------------------------------------------------------- |
| `<h5>`     | HTML의 헤딩 태그를 사용해요.            | 스크린 리더가 자동으로 제목을 인식하고 읽어줘요.                                              |
| `<button>` | HTML의 버튼 태그를 사용해요.            | 스크린 리더가 버튼이라는 요소 유형을 전달하고, 사용자는 두 번 탭하여 버튼을 실행할 수 있어요. |
| `alt=""`   | 장식용 이미지 처리가 자동으로 적용돼요. | `figure` 태그에 사용되는 이미지는 장식용으로 처리되어 스크린 리더가 읽지 않아요.              |

### 접근성 속성 적용 예시

접근성 속성이 적용되는 방법은 아래 예시를 통해 확인해 보세요.

```jsx
<Result
  figure={<Asset.Image src="example.png" />} // alt=""가 자동 적용돼요
  title="다시 시도해 주세요" // <h5> 태그로 자동 변환돼요
  description="시스템에 잠깐 문제가 생겨 화면을 불러오지 못했어요."
  button={
    <Result.Button> // <button> 태그로 자동 변환돼요
      다시 시도하기
    </Result.Button>
  }
/>
```

이러한 방법으로 `Result` 컴포넌트는 추가적인 접근성 설정 없이도 기본적인 접근성을 지원하도록 설계되었어요.

## 인터페이스

**Type: ResultProps**

```typescript
export interface ResultProps {
  /**
   * `title` 위에 표시할 시각적 요소로, 주로 아이콘이나 이미지를 나타내요. `Asset` 컴포넌트를 사용해서 다양한 시각적 콘텐츠를 표현할 수 있어요.
   */
  figure?: ReactNode;
  /**
   * 결과 화면의 제목이에요. 사용자가 어떤 작업을 한 뒤의 성공 여부 같은 상태를 간결하게 전달하는 데에 사용해요.
   */
  title?: ReactNode;
  /**
   * `title` 아래에 추가로 설명을 제공하는 영역이에요. 좀 더 자세한 정보를 제공할 때 사용해요.
   */
  description?: ReactNode;
  /**
   * `description` 아래에 표시할 버튼이에요. `Result.Button` 컴포넌트를 사용해서 다시 시도하기, 홈으로 돌아가기 등과 같은 액션을 추가할 수 있어요.
   */
  button?: ReactNode;
}
```

---

# SearchField (/tds-mobile/components/search-field/)

export function getPreviewBox(PreviewComponent) {
return (
[Preview: VirtualRoot]
);
}

# SearchField

`SearchField` 컴포넌트는 검색 입력창을 구현할 때 사용되는 컴포넌트예요. 검색 입력창에 고정 기능과 검색어 삭제 기능을 포함하며, 다양한 설정을 제공해요.

[Preview: Basic]

## 사용법

### 상단에 고정하기

`SearchField` 컴포넌트는 검색창을 화면 상단에 고정할 수 있어요. 검색창을 화면의 상단에 고정하고 싶을 때는 `fixed` 속성을 사용하면 돼요. CSS에서 `position` 속성이 `fixed`일 때와 같아요.
예를 들어, 검색창이 항상 보이게 유지해서 사용자가 쉽게 검색할 수 있도록 만들고 싶을 때 유용해요.

- `fixed`: 검색창을 화면 상단에 고정하려면 `true`로 설정하세요. 검색창이 스크롤 중에도 항상 보이게 돼요.
- `takeSpace`: 검색창이 고정될 때 페이지 빈 공간을 유지하려면 `true`로 유지하세요. `true`로 유지하면 레이아웃 변화 없이 페이지의 다른 요소들이 움직이지 않도록 할 수 있어요.

### 검색어 삭제하기

`SearchField` 컴포넌트는 기본적으로 입력된 검색어를 삭제할 수 있는 버튼을 제공해요. 사용자가 삭제 버튼을 클릭하면 입력된 내용은 지워지고, 추가적으로 `onDeleteClick` 속성을 사용해 특정 동작을 실행할 수 있어요.
이 속성을 활용하면 검색어를 삭제할 때 로그를 남기거나, 다른 동작을 실행하도록 설정할 수 있어요.

**Example: Delete**

```tsx
<div style={{ position: "relative" }}>
  <SearchField
    placeholder="검색어를 입력하고 오른쪽 버튼을 클릭해보세요."
    onDeleteClick={() => alert("delete")}
  />
</div>
```

## 인터페이스

**Type: SearchFieldProps**

```typescript
export interface SearchFieldProps {
  /**
   * 컴포넌트를 상단에 고정시켜줘요.
   * @default false
   */
  fixed?: boolean;
  /**
   * 이 값과 fixed속성이 true일 때 fixed 된 컴포넌트가 화면에서 차지하던 영역을 채워줘요.
   * @default true
   */
  takeSpace?: boolean;
  /**
   * 텍스트 삭제 아이콘을 눌렀을 때 호출되는 콜백 함수예요.
   */
  onDeleteClick?: () => void;
}
```

---

# Segmented Control (/tds-mobile/components/segmented-control/)

# Segmented Control

`SegmentedControl` 컴포넌트는 여러 선택지 중 하나를 선택할 수 있는 UI 요소예요. 주로 단일 옵션을 선택할 때 사용하고, `Radio` 컴포넌트와 같은 역할을 해요.

[Preview: Basic]

## 사용 예제

### 상태

#### 상태를 외부에서 관리하는 방식

`SegmentedControl`의 상태를 외부에서 관리하려면 `value`와 `onChange` 속성을 함께 사용하세요. 이렇게 하면 어떤 아이템이 선택되었는지를 외부에서 직접 관리할 수 있어요.

**Example: Controlled**

```tsx
function Controlled() {
  const [value, setValue] = React.useState("1");

  return (
    <SegmentedControl value={value} onChange={(value) => setValue(value)}>
      <SegmentedControl.Item value="1">아이템1</SegmentedControl.Item>
      <SegmentedControl.Item value="2">아이템2</SegmentedControl.Item>
      <SegmentedControl.Item value="3">아이템3</SegmentedControl.Item>
    </SegmentedControl>
  );
}
```

#### 상태를 내부에서 관리하는 방식

`SegmentedControl`의 상태를 내부에서 자동으로 관리하려면 `defaultValue` 속성을 사용하세요. 이 속성은 `SegmentedControl`가 처음 화면에 표시될 때 선택될 `SegmentedControl.Item`의 `value` 속성을 정해주고, 그 후에는 컴포넌트가 스스로 상태를 관리해요. 이 방식은 상태 변화를 추적할 필요가 없을 때 유용해요.

**Example: Uncontrolled**

```tsx
<SegmentedControl defaultValue="1">
  <SegmentedControl.Item value="1">아이템1</SegmentedControl.Item>
  <SegmentedControl.Item value="2">아이템2</SegmentedControl.Item>
  <SegmentedControl.Item value="3">아이템3</SegmentedControl.Item>
</SegmentedControl>
```

### 크기 조정하기

`SegmentedControl` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. `small`, `large` 중 하나를 선택할 수 있어요.

**Example: Sizes**

```tsx
<div style={{ display: "flex", flexDirection: "column", gap: "10px" }}>
  <SegmentedControl size="small" defaultValue="1">
    <SegmentedControl.Item value="1">아이템1</SegmentedControl.Item>
    <SegmentedControl.Item value="2">아이템2</SegmentedControl.Item>
    <SegmentedControl.Item value="3">아이템3</SegmentedControl.Item>
  </SegmentedControl>
  <SegmentedControl size="large" defaultValue="1">
    <SegmentedControl.Item value="1">아이템1</SegmentedControl.Item>
    <SegmentedControl.Item value="2">아이템2</SegmentedControl.Item>
    <SegmentedControl.Item value="3">아이템3</SegmentedControl.Item>
  </SegmentedControl>
</div>
```

### 스크롤 되게 하기

`SegmentedControl.Item`의 개수나 글자 수가 많다면 `alignment` 속성을 `fluid`로 설정해 보세요. 이렇게 하면 아이템의 너비가 내용에 맞춰 조정되고, `SegmentedControl` 컴포넌트에 가로 스크롤이 생겨요.

스크롤해서 첫 번째 아이템이 가려질 때 왼쪽 화살표 버튼이 나타나고, 클릭하면 첫 번째 아이템이 보이게 스크롤돼요.

**Example: Fluid**

```tsx
<SegmentedControl defaultValue="1" alignment="fluid">
  {Array.from({ length: 20 }, (_, index) => (
    <SegmentedControl.Item
      key={index}
      value={String(index + 1)}
    >{`아이템${index + 1}`}</SegmentedControl.Item>
  ))}
</SegmentedControl>
```

## 접근성

`SegmentedControl` 컴포넌트는 기본적으로 접근성을 지원하는 여러 속성을 포함하고 있어요. 이 속성들은 스크린 리더 사용자들이 컴포넌트를 명확하게 이해하고 상호작용할 수 있도록 도와줘요.

### 기본 접근성 지원

`SegmentedControl` 컴포넌트는 다음과 같은 접근성 기능을 기본적으로 가지고 있어요. 그래서 개발자는 별도의 설정 없이도 사용자의 접근성을 고려한 형태의 `SegmentedControl` 컴포넌트를 제공할 수 있어요.

| 속성                                                                                                                 | 접근성 효과                                                                                      | 설명                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| [`role="radiogroup"`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/radiogroup_role)         | 스크린 리더에서 "라디오 그룹"으로 인식해요.                                                      | 여러 항목 중 하나만 선택할 수 있는 그룹이라는 것을 명확히 전달해요.                                                             |
| [`role="radio"`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/radio_role) 및 `tabindex="0"` | 스크린 리더에서 각 항목을 "라디오 버튼"으로 인식해요.                                            | 라디오 버튼으로 인식되며, 각 항목의 선택 가능성을 전달해요.                                                                     |
| [`aria-checked`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-checked)            | 선택된 항목의 상태를 스크린 리더에서 알려줘요.                                                   | 선택 상태에 따라 `aria-checked` 속성이 자동으로 업데이트되며, `true`일 때는 "선택됨", `false`일 때는 "선택 안 됨"으로 읽어줘요. |
| [`aria-labelledby`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby)      | 모든 상호 작용 가능한 요소는 접근성 레이블이 필요하며, 이를 `aria-labelledby` 속성으로 지원해요. | 레이블이 `role="radio"` 요소와 분리되어 있지만, `aria-labelledby`로 자동 적용돼요.                                              |

[`aria-checked`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-checked) 속성은 선택 상태에 따라 자동으로 관리돼요.  
개발자가 선택 상태만 업데이트하거나, 내부 상태 관리를 사용하면 컴포넌트가 `aria-checked` 속성을 자동으로 설정하여 스크린 리더 사용자에게 현재 상태를 정확히 전달해요.
이러한 속성들은 `SegmentedControl` 컴포넌트에 기본적으로 적용되며, 사용자가 선택 상태를 명확히 이해할 수 있도록 도와요.

## 인터페이스

**Type: SegmentedControlProps**

```typescript
export interface SegmentedControlProps {
  /**
   * `SegmentedControl` 컴포넌트를 구성하는 하나 이상의 `SegmentedControl.Item` 컴포넌트를 받아요. `SegmentedControl.Item` 컴포넌트는 각각의 아이템을 나타내며, 여러 개의 아이템을 배열로 전달할 수 있어요.
   */
  children: ReactNode;
  /**
   * `SegmentedControl` 컴포넌트의 크기를 결정해요.
   *
   * @default 'small'
   */
  size?: "small" | "large";
  /**
   * 이 값이 `fluid`면 `SegmentedControl.Item` 컴포넌트의 너비가 글자 수에 맞춰져요. `SegmentedControl.Item` 컴포넌트의 전체 크기가 `SegmentedControl` 컴포넌트의 컨테이너를 넘어가면 가로 스크롤이 생겨요.
   *
   * @default 'fixed'
   */
  alignment?: "fixed" | "fluid";
  /**
   * 이 값을 가지는 `SegmentedControl.Item` 컴포넌트가 선택된 상태로 표현돼요. 주로 `SegmentedControl` 컴포넌트의 상태를 컴포넌트 외부에서 관리할 때, `onChange` 속성과 함께 사용해요.
   */
  value?: string;
  /**
   * `SegmentedControl` 컴포넌트의 상태를 컴포넌트 내부에서 관리할 때, 초기 선택 값을 지정해요.
   */
  defaultValue?: string;
  /**
   * `SegmentedControl` 컴포넌트의 선택 상태가 바뀔 때 실행되는 함수예요.
   */
  onChange?: (v: string) => void;
}
```

**Type: SegmentedControlItemProps**

```typescript
export interface SegmentedControlItemProps {
  /**
   * `SegmentedControl.Item`의 라벨을 표현해요.
   */
  children: ReactNode;
  /**
   * 사이즈에 따라 `SegmentedControl.Item` 컴포넌트의 텍스트 크기와 패딩이 변경돼요.
   */
  size?: "small" | "large";
  /**
   * 해당 `SegmentedControl.Item`을 선택했을 때, `SegmentedControl` 컴포넌트의 `onChange` 속성에 전달되는 값이에요.
   */
  value: string;
}
```

---

# Skeleton (/tds-mobile/components/skeleton/)

# Skeleton

`Skeleton` 컴포넌트는 데이터가 로드되는 동안 콘텐츠의 기본 레이아웃을 임시로 보여 주는 컴포넌트예요. 사용자가 빈 화면 대신 콘텐츠 구조를 미리 볼 수 있어요.
덕분에 사용자는 로딩 중이라는 인식을 할 수 있고, 페이지가 느리게 로딩될 때도 사용자 경험을 높이는 데 도움이 돼요.

[Preview: Basic]

## 사용법

### 패턴 사용하기

`Skeleton` 컴포넌트는 자주 사용하는 레이아웃을 쉽게 설정할 수 있도록 미리 정의된 패턴을 제공해요. 다음 패턴 중 필요한 것을 선택해서 사용할 수 있어요.

- `topList`: 제목이 상단에 있는 리스트예요.
- `topListWithIcon`: 제목이 상단에 있고 아이콘이 포함된 리스트예요.
- `amountTopList`: 제목과 부제목이 상단에 있는 리스트예요.
- `amountTopListWithIcon`: 제목과 부제목이 상단에 있고 아이콘이 포함된 리스트예요.
- `subtitleList`: 부제목이 포함된 리스트예요.
- `subtitleListWithIcon`: 부제목과 아이콘이 포함된 리스트예요.
- `listOnly`: 리스트 형태만 있는 패턴이에요.
- `listWithIconOnly`: 아이콘이 포함된 리스트예요.
- `cardOnly`: 카드 형태만 있는 패턴이에요.

각 패턴을 선택하면 `Skeleton`이 자동으로 해당 레이아웃에 맞는 구조로 렌더링돼요. 필요한 패턴을 선택해서 바로 적용해 볼 수 있어요.

**Example: TopListWithIcon**

```tsx

```

### 커스텀 패턴 사용하기

기본적으로 제공되는 패턴 외에도 사용자 정의 패턴을 활용해서 원하는 레이아웃을 자유롭게 설정할 수 있어요.
커스텀 패턴을 사용할 때는 `custom` 속성에 배열 형태로 패턴을 정의할 수 있고, 다양한 타입을 조합해서 레이아웃을 구성할 수 있어요. 각 타입은 다음과 같아요.

- `title`: 제목에 해당하는 굵고 큰 스켈레톤 바예요. 일반적으로 상단에 배치해서 제목의 위치를 표현할 때 사용해요.
- `subtitle`: 제목보다 얇은 부제목용 스켈레톤 바예요. 제목 아래에 위치할 때 사용하면 좋아요.
- `list`: 리스트 형태의 스켈레톤이에요. 여러 줄의 가로형 바(bar)로 이루어져 있어서, 데이터 목록을 미리 보여줄 때 유용해요.
- `listWithIcon`: 아이콘과 함께 리스트 형태로 구성된 스켈레톤이에요. 각 아이템 왼쪽에 아이콘의 위치를 미리 시각화할 수 있어요.
- `card`: 카드 형태의 스켈레톤이에요. 직사각형 블록으로, 카드 레이아웃을 미리 보여줄 때 적합해요.
- `spacer(${number})`: 지정한 픽셀 수만큼의 빈 공간을 추가하는 타입이에요. `spacer(20)`처럼 숫자를 넣어 빈 공간을 조절할 수 있어요. 각 요소 간의 여백을 맞출 때 유용해요.

**Example: CustomPattern**

```tsx

```

### 반복 설정하기

`repeatLastItemCount` 속성을 사용하면 `Skeleton` 컴포넌트가 마지막 요소를 반복해서 렌더링하게 할 수 있어요.
이 속성에는 반복할 개수를 숫자로 지정하거나, 무한 반복을 위해 `'infinite'` 값을 사용할 수 있어요.
단, `'infinite'` 값을 설정할 경우 실제로는 마지막 요소가 최대 30번 반복돼요. 아무 값도 설정하지 않으면 기본값으로 3번 반복돼요.

**Example: Repeat**

```tsx

```

### 배경 설정하기

`Skeleton` 컴포넌트는 `background` 속성으로 배경 색상을 설정할 수 있어요.
배경 색상은 로딩 중인 화면의 전체적인 느낌을 조절하는 데 유용해요. 설정할 수 있는 배경 색상은 다음과 같아요.

- `white`: 흰색 배경이에요. 어두운 배경에서 로딩 상태를 표현할 때 적합해요.
- `grey`: 회색 배경으로, 일반적인 로딩 화면에 많이 사용돼요.
- `greyOpacity100`: 불투명한 진한 회색 배경이에요. 밝은 배경에서 로딩 화면을 강조하고 싶을 때 유용해요.

**Example: Background**

```tsx
<div style={{ background: adaptive.grey300 }}></div>
```

## 인터페이스

**Type: SkeletonProps**

```typescript
export interface SkeletonProps {
  /**
   * `Skeleton` 컴포넌트의 전체 높이를 설정해요.
   * @default auto
   */
  height?: number | string;
  /**
   * 미리 정의된 패턴으로 `Skeleton` 컴포넌트의 레이아웃을 설정해요.
   *
   * - `topList`: 제목이 상단에 있는 리스트예요.
   * - `topListWithIcon`: 제목이 상단에 있고 아이콘이 포함된 리스트예요.
   * - `amountTopList`: 제목과 부제목이 상단에 있는 리스트예요.
   * - `amountTopListWithIcon`: 제목과 부제목이 상단에 있고 아이콘이 포함된 리스트예요.
   * - `subtitleList`: 부제목이 포함된 리스트예요.
   * - `subtitleListWithIcon`: 부제목과 아이콘이 포함된 리스트예요.
   * - `listOnly`: 리스트 형태만 있는 패턴이에요.
   * - `listWithIconOnly`: 아이콘이 포함된 리스트예요.
   * - `cardOnly`: 카드 형태만 있는 패턴이에요.
   * @default topList
   */
  pattern?:
    | "topList"
    | "topListWithIcon"
    | "amountTopList"
    | "amountTopListWithIcon"
    | "subtitleList"
    | "subtitleListWithIcon"
    | "listOnly"
    | "listWithIconOnly"
    | "cardOnly";
  /**
   * 사용자 정의 패턴으로 `Skeleton` 컴포넌트의 레이아웃을 설정해요.
   *
   * - `title`: 제목에 해당하는 굵고 큰 스켈레톤 바예요.
   * - `subtitle`: 제목보다 얇은 부제목용 스켈레톤 바예요.
   * - `list`: 리스트 형태의 스켈레톤이에요.
   * - `listWithIcon`: 아이콘과 함께 리스트 형태로 구성된 스켈레톤이에요.
   * - `card`: 카드 형태의 스켈레톤이에요.
   * - `spacer(${number})`: 지정한 픽셀 수만큼의 빈 공간을 추가하는 타입이에요. 숫자를 넣어 공간을 조절할 수 있어요.
   */
  custom?: Array<
    | "list"
    | "title"
    | "subtitle"
    | "card"
    | "listWithIcon"
    | `spacer(${number})`
  >;
  /**
   * "infinite"이면 마지막 모듈을 30번 반복해요.
   * @default 3
   */
  repeatLastItemCount?: number | "infinite";
  /**
   * `Skeleton` 컴포넌트의 표시 상태를 설정해요.
   * @default show
   */
  play?: "show" | "hide";
  /**
   * `Skeleton` 컴포넌트의 색상을 설정해요.
   * @default grey
   */
  background?: "white" | "grey" | "greyOpacity100";
}
```

---

# Slider (/tds-mobile/components/slider/)

# Slider

`Slider` 컴포넌트는 막대를 좌우로 움직여서 원하는 숫자를 선택할 수 있는 컨트롤이에요. 주어진 범위 내에서 핸들을 드래그하여 원하는 값을 선택할 수 있어요.
숫자의 범위를 시각적으로 표현하고 직관적으로 조절해야 하는 상황에서 유용하게 사용할 수 있어요.

[Preview: Basic]

## 사용법

### 색상 변경하기

`color` 속성을 사용하여 슬라이더의 트랙 색상을 변경할 수 있어요. 색상을 변경하면 슬라이더의 시각적 피드백을 강화하거나, 특정 상태나 의미를 전달할 때 유용해요.
CSS 색상 값을 지정할 수 있으며, 기본값은 `blue400` 색상이에요.

**Example: SliderWithColor**

```tsx
function SliderWithColor() {
  const [value, setValue] = React.useState(50);
  const [value2, setValue2] = React.useState(50);
  const [value3, setValue3] = React.useState(50);

  return (
    <div style={{ display: "flex", flexDirection: "column", gap: "10px" }}>
      <Slider
        color={adaptive.blue500}
        value={value}
        onValueChange={(newValue) => setValue(newValue)}
      />
      <Slider
        color={adaptive.green500}
        value={value2}
        onValueChange={(newValue) => setValue2(newValue)}
      />
      <Slider
        color={adaptive.red500}
        value={value3}
        onValueChange={(newValue) => setValue3(newValue)}
      />
    </div>
  );
}
```

### 라벨 사용하기

`label` 속성을 사용하여 슬라이더 아래에 최소값, 최대값, 중간값을 표시할 수 있어요. 슬라이더의 범위를 명확하게 표시하고 싶을 때 유용해요.
아래 예시처럼 가격 범위를 선택하는 슬라이더에서 최소 금액과 최대 금액을 표시할 때 활용할 수 있어요. 중간값을 표시하면 사용자가 원하는 값을 더 쉽게 찾을 수 있어요.

**Example: SliderWithLabel**

```tsx
function SliderWithLabel() {
  const [value, setValue] = React.useState(150);

  const MIN = 100;
  const MID = 150;
  const MAX = 200;

  return (
    <Slider
      value={value}
      minValue={MIN}
      maxValue={MAX}
      label={{ min: `${MIN} 만원`, mid: `${MID} 만원`, max: `${MAX} 만원` }}
      onValueChange={(newValue) => setValue(newValue)}
    />
  );
}
```

### 툴팁 사용하기

`tooltip` 속성을 사용하여 슬라이더 위에 현재 값을 표시할 수 있어요. 툴팁은 사용자가 슬라이더를 조작할 때 현재 선택된 값을 실시간으로 보여주어 더 정확한 값을 선택하는 데 도움을 줘요.
특히 정밀한 값 조절이 필요하거나, 슬라이더의 현재 값을 명확하게 보여줘야 하는 상황에서 유용해요.

`Slider.Tooltip` 컴포넌트를 사용하면 슬라이더의 현재 값을 툴팁으로 표시할 수 있어요.
이 컴포넌트는 `Tooltip` 컴포넌트의 속성을 그대로 사용할 수 있어서, `offset` 속성으로 툴팁의 위치를 조절하거나 다양한 스타일을 적용할 수 있어요.
슬라이더의 현재 값을 툴팁 메시지로 표시하려면 `message` 속성에 값을 전달해야 해요.

**Example: SliderWithTooltip**

```tsx
function SliderWithTooltip() {
  const [value, setValue] = React.useState(50);

  return (
    <div style={{ paddingTop: '55px' }}>
      }
        onValueChange={(newValue) => setValue(newValue)}
      />
    </div>
  );
}
```

## 인터페이스

**Type: SliderProps**

```typescript
export interface SliderProps {
  /**
   * `Slider` 컴포넌트의 현재 값을 설정해요. 정의되지 않으면 사용자의 이벤트에 따라 값이 변경돼요.
   */
  value?: number;
  /**
   * `Slider` 컴포넌트의 기본값을 설정해요. 정의되지 않으면 사용자의 이벤트에 따라 값이 변경돼요.
   */
  defaultValue?: number;
  /**
   * `value`가 변경될 때 호출되는 함수에요.
   */
  onValueChange?: (value: number) => void;
  /**
   * `value`의 최솟값을 설정해요.
   */
  minValue?: number;
  /**
   * `value`의 최댓값을 설정해요.
   */
  maxValue?: number;

  /**
   * `Slider` 컴포넌트의 트랙 색상을 변경해요.
   */
  color?: string;
  /**
   * `Slider` 컴포넌트 아래에 표시될 라벨을 설정해요.
   */
  label?: {
    /**
     * 최솟값에 표시될 텍스트에요.
     */
    min: string;
    /**
     * 최댓값에 표시될 텍스트에요.
     */
    max: string;
    /**
     * 중간값에 표시될 텍스트에요.
     */
    mid?: string;
  };
  /**
   * `Slider` 컴포넌트 위에 표시될 툴팁을 설정해요.
   */
  tooltip?: React.ReactElement;
}
```

**Type: SliderTooltipProps**

```typescript
export interface SliderTooltipProps extends TooltipProps {
  /**
   * 툴팁 메시지에 표시될 텍스트에요.
   */
  message: string;
}
```

---

# Stepper (/tds-mobile/components/stepper/)

# Stepper

`Stepper` 컴포넌트는 여러 단계를 시각적으로 보여줄 때 사용하는 컴포넌트예요. 각 단계는 제목과 설명을 가질 수 있고, 오른쪽에는 아이콘이나 버튼을 추가할 수 있어요. 순차적인 흐름을 사용자에게 쉽게 전달하는 데 적합해요.

[Preview: Basic]

## 사용법

### 단계 추가하기

`StepperRow` 컴포넌트의 `content` 속성에 `StepperRow.Texts` 컴포넌트를 사용해서 단계를 추가할 수 있어요.

#### 제목과 설명 추가하기

`StepperRow.Texts` 컴포넌트에서 `type` 속성을 사용하면 제목과 설명의 스타일을 변경할 수 있어요.

- `A`: 일반 크기의 제목(`t5`), 일반 크기의 설명(`t6`)
- `B`: 큰 크기의 제목(`t4`), 일반 크기의 설명(`t6`)
- `C`: 일반 크기의 제목(`t5`), 작은 크기의 설명(`t7`)

**Example: Center**

```tsx
<>
  }
    center={}
  />
  }
    center={}
  />
  }
    center={}
    hideLine
  />
</>
```

### 왼쪽에 요소 추가하기

`StepperRow` 컴포넌트의 `left` 속성을 사용하면 콘텐츠 영역의 왼쪽에 요소를 배치할 수 있어요. 보통 단계를 나타내기 위한 숫자나 의미를 부각하는 아이콘을 배치하는 데 많이 사용해요.

#### 왼쪽에 숫자 아이콘 추가하기

`Stepper.NumberIcon` 컴포넌트를 사용해 왼쪽에 숫자 아이콘을 추가할 수 있어요. 각 단계를 명확히 구분할 수 있어 유용해요.

**Example: LeftNumberIcon**

```tsx
<>
  }
    center={}
  />
  }
    center={}
  />
  }
    center={}
    hideLine
  />
</>
```

#### 왼쪽에 에셋 추가하기

`Asset` 컴포넌트를 사용해서 왼쪽에 원하는 에셋을 추가할 수 있어요. `Stepper` 컴포넌트의 여백 규칙을 지키려면 `Asset` 컴포넌트를 `Stepper.AssetFrame` 컴포넌트로 감싸서 사용하면 돼요.

**Example: LeftAsset**

```tsx
<>
  }
        backgroundColor="transparent"
      />
    }
    center={}
  />
  }
        backgroundColor="transparent"
      />
    }
    center={}
  />
  }
        backgroundColor="transparent"
      />
    }
    center={}
    hideLine
  />
</>
```

### 오른쪽에 요소 추가하기

`StepperRow` 컴포넌트의 `right` 속성을 사용해서 콘텐츠 영역의 오른쪽에 요소를 추가할 수 있어요.

#### 오른쪽에 화살표 아이콘 추가하기

`Stepper.RightArrow` 컴포넌트를 사용해서 오른쪽에 화살표 아이콘을 추가할 수 있어요.

**Example: RightArrow**

```tsx
<>
  }
    center={}
    right={}
  />
  }
    center={}
    right={}
  />
  }
    center={}
    right={}
    hideLine
  />
</>
```

#### 오른쪽에 버튼 추가하기

`Stepper.RightButton` 컴포넌트를 사용해서 오른쪽에 버튼을 추가할 수 있어요.

**Example: RightButton**

```tsx
<>
  }
    center={}
    right={<StepperRow.RightButton>버튼</StepperRow.RightButton>}
  />
  }
    center={}
    right={<StepperRow.RightButton>버튼</StepperRow.RightButton>}
  />
  }
    center={}
    right={<StepperRow.RightButton>버튼</StepperRow.RightButton>}
    hideLine
  />
</>
```

### 연결선 가리기

`StepperRow` 컴포넌트의 `hideLine` 속성을 사용하면 연결선을 숨길 수 있어요. 주로 마지막 단계에서 연결선을 제거할 때 사용해요.

**Example: HideLine**

```tsx
<>
  }
    center={}
  />
  }
    center={}
    hideLine
  />
</>
```

### 등장 모션 제공하기

`Stepper` 컴포넌트를 사용해 `StepperRow` 컴포넌트를 감싸면, 모션을 적용할 수 있어요. 이 모션은 각 스텝이 차례로 등장하게 해서 사용자가 단계를 쉽게 인식할 수 있게 도와줘요. `Stepper`로 감싸면 자식으로 전달된 `StepperRow`들이 순차적으로 등장해요.

**Example: Basic**

```tsx
<Stepper>
  }
    center={}
    right={}
  />
  }
    center={}
    right={}
  />
  }
    center={}
    right={}
    hideLine
  />
</Stepper>
```

`staggerDelay` 속성을 사용하면 스텝들이 일정한 시간 간격을 두고 순차적으로 등장하는 애니메이션을 적용할 수 있어요. stagger는 각 요소가 동시에 등장하지 않고, 일정한 딜레이를 두고 차례로 등장하는 방식이에요. 이 방식은 복잡한 정보나 여러 단계를 시각적으로 더 쉽게 인식할 수 있게 도와줘요.

`staggerDelay` 값은 초 단위로 입력하며, 이 값이 클수록 각 스텝 사이의 등장 간격이 길어져요. 예를 들어, `staggerDelay={0.5}`로 설정하면 각 스텝이 0.5초 간격으로 순차적으로 나타나요.

**Example: StepperStaggerDelay**

```tsx
<Stepper staggerDelay={0.5}>
  }
    center={}
  />
  }
    center={}
  />
  }
    center={}
    hideLine
  />
</Stepper>
```

`Stepper` 컴포넌트의 `play` 속성으로 처음 렌더링될 때 모션을 재생할지 결정할 수 있어요. `play`를 토글해도 한 번 실행된 모션은 다시 실행되지 않아요. `play`가 `false`라면 모션이 실행되지 않아요.

**Example: StepperPlay**

```tsx
<Stepper play={false}>
  }
    center={}
  />
  }
    center={}
  />
  }
    center={}
    hideLine
  />
</Stepper>
```

## 인터페이스

**Type: StepperProps**

```typescript
export interface StepperProps {
  /**
   * `Stepper` 컴포넌트가 렌더링될 때 `StepperRow` 컴포넌트의 등장 애니메이션을 실행해요.
   * `false`라면 애니메이션 없이 렌더링돼요.
   * @default true
   */
  play?: boolean;

  /**
   * 애니메이션의 시작 지연 시간을 설정해요. 초 단위를 사용해요.
   * @default 0
   */
  delay?: number;

  /**
   * 각 `StepperRow` 컴포넌트가 순차적으로 나타날 때 간격을 설정해요. 초 단위를 사용해요.
   * @default 0.1
   */
  staggerDelay?: number;
}
```

**Type: StepperRowProps**

```typescript
export interface StepperRowProps {
  /**
   * `StepperRow` 컴포넌트의 왼쪽 영역에 표시될 컴포넌트를 지정해요. 주로 아이콘이나 이미지가 사용돼요.
   */
  left: ReactNode;

  /**
   * `StepperRow` 컴포넌트의 중앙 영역에 표시될 타이틀과 설명을 지정해요. 주로 텍스트가 들어가요.
   */
  center: ReactNode;

  /**
   * `StepperRow` 컴포넌트의 오륵쪽 영역에 표시될 컴포넌트를 지정해요. 주로 버튼이나 아이콘가 사용돼요.
   */
  right?: ReactNode;

  /**
   * `StepperRow` 컴포넌트의 연결선을 숨길지 여부를 설정해요. 주로 마지막 스텝에서 `true`를 사용하여 연결선을 제거해요.
   * @default false
   */
  hideLine?: boolean;
}
```

**Type: StepperRowAssetFrameProps**

```typescript
export interface StepperRowAssetFrameProps extends Asset.FrameProps {
  /**
   * `Asset` 컴포넌트의 프레임 형태를 지정해요. 주로 `Asset`에서 제공하는 preset을 사용해요.
   */
  shape: Asset.FrameShapeType; // todo: Asset 링크 추가하기

  /**
   * `Asset` 컴포넌트의 프레임 안에 표시될 콘텐츠를 지정해요. 주로 이미지나 아이콘을 추가해요.
   */
  content: ReactNode;
}
```

**Type: StepperRowNumberIconProps**

```typescript
export interface StepperRowNumberIconProps extends IconProps {
  /**
   * `StepperRow` 컴포넌트 왼쪽에 순서를 나타내는 숫자를 설정해요.
   */
  number: 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9;
}
```

**Type: StepperRowRightArrowProps**

```typescript
export interface StepperRowRightArrowProps {
  /**
   * 아이콘의 이름을 지정해요.
   * @default 'icon-arrow-right-mono'
   */
  name?: string;

  /**
   * 아이콘의 색상을 지정해요.
   * @default adaptive.grey400
   */
  color?: string;

  /**
   * 프레임의 모양을 설정해요.
   * 더 큰 텍스트 스케일이 160보다 크거나 같으면, `Asset.frameShape.CleanW32` 로 자동 변경돼요.
   * @default Asset.frameShape.CleanW24
   */
  frameShape?: Asset.FrameShapeType; // todo: Asset 링크 추가하기
}
```

**Type: StepperRowRightButtonProps**

```typescript
export interface StepperRowRightButtonProps extends ButtonProps {
  /**
   * 버튼의 크기를 설정해요.
   * @default 'small'
   */
  size?: "small" | "medium" | "large" | "xlarge";

  /**
   * 버튼의 컬러를 설정해요.
   * @default 'primary'
   */
  color?: "primary" | "danger" | "light" | "dark";
}
```

**Type: StepperRowTextsProps**

```typescript
export interface StepperRowTextsProps {
  /**
   * `StepperRow` 컴포넌트의 텍스트의 타입을 설정해요. 타이틀과 설명의 스타일이 타입에 따라 달라져요.
   * - `A`일 떄 타이틀은 `t5`, 설명은 `t6`에요.
   * - `B`일 떄 타이틀은 `t4`, 설명은 `t6`에요.
   * - `C`일 떄 타이틀은 `t5`, 설명은 `t7`에요.
   */
  type: "A" | "B" | "C";

  /**
   * `StepperRow` 컴포넌트에 표시될 타이틀을 지정해요.
   */
  title: ReactNode;

  /**
   * `StepperRow` 컴포넌트에 표시될 설명을 지정해요.
   */
  description?: ReactNode;

  /**
   * 추가로 타이틀의 스타일링을 할 때 사용해요.
   */
  titleProps?: ParagraphTextProps; // todo: Paragraph 링크 추가하기

  /**
   * 추가로 설명의 스타일링을 할 때 사용해요.
   */
  descriptionProps?: ParagraphTextProps; // todo: Paragraph 링크 추가하기
}
```

---

# Switch (/tds-mobile/components/switch/)

# Switch

`Switch` 컴포넌트는 두 가지 상태(예: 켜짐/꺼짐, 활성화/비활성화)를 전환할 수 있는 UI 요소예요. 단순한 토글 방식으로 동작해서 주로 설정이나 옵션을 활성화하거나 비활성화할 때 사용해요. 체크박스와 비슷하지만 더 직관적인 시각적 요소로 사용자가 상태 변화를 쉽게 인식할 수 있어요.

[Preview: Basic]

## 사용 예제

### 상태

스위치의 켜짐과 꺼짐 상태를 표현하려면 `checked` 속성을 사용하세요. 상태를 바꾸려면 `onChange` 속성과 함께 사용하세요.

**Example: States**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

### 비활성화하기

스위치를 비활성화하려면 `disabled` 속성을 사용하세요. 비활성화된 스위치는 사용자가 클릭할 수 없고, 시각적으로도 비활성화된 상태임을 나타내요.

**Example: Disables**

```tsx
<div style={{ display: "flex", gap: "8px" }}></div>
```

### 터치 애니메이션 끄기

스위치를 클릭했을 때 나타나는 터치 애니메이션을 제외하려면 `hasTouchEffect` 속성에 `false`를 넣어주세요.

**Example: Effects**

```tsx
function Effects() {
  const [checked, setChecked] = React.useState(true);

  return (
    <Switch
      hasTouchEffect={false}
      checked={checked}
      onChange={() => setChecked((prev) => !prev)}
    />
  );
}
```

## 접근성

`Switch` 컴포넌트는 다음과 같이 기본적인 접근성을 제공해요. 덕분에 별도의 설정 없이도 기본적으로 사용자의 접근성을 고려한 형태의 `Switch` 컴포넌트를 제공할 수 있어요.

| 속성                                                                                                        | 접근성 효과                                      | 설명                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------- |
| [`role="switch"`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/switch_role)        | 스크린 리더에서 "전환" 또는 "스위치"로 인식해요. | 스위치 역할을 명확히 전달해서 사용자가 상호작용 가능하다는 것을 알 수 있어요. |
| [`aria-checked`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-checked)   | 켜짐 또는 꺼짐 상태를 스크린 리더에서 읽어줘요.  | `checked` 상태에 따라 `aria-checked` 상태가 자동으로 업데이트돼요.            |
| [`aria-disabled`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-disabled) | 비활성화된 상태를 스크린 리더에서 읽어줘요.      | 스위치가 비활성화되어 상호작용할 수 없다는 정보를 스크린 리더로 알려줘요.     |

```jsx
<Switch checked={isOn} onChange={handleToggle} />
```

### 추가로 지원해야 하는 접근성

개발자가 접근성을 고려해서 다음 내용을 추가로 작업해야 할 때도 있어요. 예를 들어 `Switch` 컴포넌트를 나타내는 텍스트가 컴포넌트 바깥에 따로 있거나, 아이콘만 있다면 컴포넌트에서 제공하는 기본적인 접근성으로는 충분하지 않아요.

이럴 때는 반드시 `aria-label` 속성을 사용해서 `Switch` 컴포넌트의 역할을 설명해야 해요. 이때, 레이블에는 "스위치", "켜짐", "꺼짐" 같은 정보는 포함하지 않아요. 이러한 정보는 컴포넌트의 상태를 나타낼 뿐, 역할을 설명하지 않기 때문이에요.

```jsx
<Switch
  checked={isDarkMode}
  onChange={toggleDarkMode}
  aria-label="다크 모드"
/>
<Switch
  checked={isNotificationsEnabled}
  onChange={toggleNotifications}
  aria-label="알림 설정"
/>
```

## 인터페이스

**Type: SwitchProps**

```typescript
export interface SwitchProps {
  /**
   * `Switch` 컴포넌트의 켜짐과 꺼짐 상태를 표현해요. 상태를 바꾸려면 `onChange`에 적절한 핸들러를 전달해야 해요. (예: `setState`)
   */
  checked?: boolean;
  /**
   * 이 값이 `true`일 때 컴포넌트가 비활성화돼요.
   *
   * @default false
   */
  disabled?: boolean;
  /**
   * input 태그의 `name` 속성을 결정해요.
   */
  name?: string;
  /**
   * 이 값이 `false`라면 클릭했을 때 터치 애니메이션이 실행되지 않아요.
   *
   * @default true
   */
  hasTouchEffect?: boolean;
  /**
   * `Switch` 컴포넌트가 켜지거나 꺼질 때 실행되는 함수예요.
   */
  onChange?: (
    event: React.ChangeEvent<HTMLInputElement>,
    checked: boolean,
  ) => void;
  /**
   * `Switch` 컴포넌트를 클릭했을 때 실행되는 함수예요.
   */
  onClick?: (event: React.MouseEvent<HTMLInputElement>) => void;
}
```

---

# Tab (/tds-mobile/components/tab/)

# Tab

[Image: Tab thumbnail - tab/Thumbnail-Tab.png]

`Tab` 컴포넌트는 여러 콘텐츠를 한 화면에서 효율적으로 전환할 수 있도록 도와줘요. 각 탭은 콘텐츠 목록을 보여주고, 사용자가 선택한 탭에 따라 해당 콘텐츠를 전환해요. `Tab` 컴포넌트를 사용하면 여러 콘텐츠를 한 번에 볼 수 있고, 전환도 간편하게 할 수 있어요.

[Preview: Basic]

## 사용 예제

### 크기 조정하기

`Tab` 컴포넌트의 크기를 변경하려면 `size` 속성을 사용하세요. `small`, `large` 중 하나를 선택할 수 있어요.

**Example: Sizes**

```tsx
function Sizes() {
  const [selectedSmall, setSelectedSmall] = React.useState(0);
  const [selectedLarge, setSelectedLarge] = React.useState(0);

  return (
    <div style={{ display: "flex", flexDirection: "column", gap: 8 }}>
      <Tab size="small" onChange={(index) => setSelectedSmall(index)}>
        <Tab.Item selected={selectedSmall === 0}>small</Tab.Item>
        <Tab.Item selected={selectedSmall === 1}>small</Tab.Item>
      </Tab>
      <Tab size="large" onChange={(index) => setSelectedLarge(index)}>
        <Tab.Item selected={selectedLarge === 0}>large</Tab.Item>
        <Tab.Item selected={selectedLarge === 1}>large</Tab.Item>
      </Tab>
    </div>
  );
}
```

### 간격 조정하기

`Tab.Item` 컴포넌트들의 간격을 변경하려면 `itemGap` 속성을 사용하세요.

**Example: ItemGap**

```tsx
function ItemGap() {
  const [selected, setSelected] = React.useState(0);

  return (
    <div style={{ display: "flex" }}>
      <Tab itemGap={36} onChange={(index) => setSelected(index)}>
        <Tab.Item selected={selected === 0}>탭1</Tab.Item>
        <Tab.Item selected={selected === 1}>탭2</Tab.Item>
        <Tab.Item selected={selected === 2}>탭3</Tab.Item>
        <Tab.Item selected={selected === 3}>탭4</Tab.Item>
        <Tab.Item selected={selected === 4}>탭5</Tab.Item>
      </Tab>
    </div>
  );
}
```

### 스크롤 되게 하기

아이템이 4개 이상이면 `fluid` 속성을 사용해보세요. 아이템이 많아지면 탭에 가로 스크롤이 생겨요.

**Example: Fluid**

```tsx
function Fluid() {
  const [selected, setSelected] = React.useState(0);

  return (
    <Tab fluid onChange={(index) => setSelected(index)}>
      {Array.from({ length: 20 }, (_, index) => (
        <Tab.Item key={index} selected={selected === index}>
          {index === 0 ? "탭1" : "긴텍스트"}
        </Tab.Item>
      ))}
    </Tab>
  );
}
```

## 접근성

`Tab` 컴포넌트는 기본적인 접근성을 제공해요.

### 기본 접근성 지원

`Tab` 컴포넌트는 다음과 같은 접근성 기능을 기본적으로 가지고 있어요. 덕분에 별도의 설정 없이도 기본적으로 사용자의 접근성을 고려한 형태의 `Tab` 컴포넌트를 제공할 수 있어요.

| 속성             | 접근성 효과                                | 설명                                                                                        |
| ---------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------- |
| `role="tablist"` | 스크린 리더에서 "탭 목록"으로 인식해요.    | 탭 컨테이너의 역할을 명확히 전달해요.                                                       |
| `role="tab"`     | 스크린 리더에서 "탭"으로 인식해요.         | 각 탭의 역할을 명확히 전달해요.                                                             |
| `aria-selected`  | 현재 선택된 탭을 스크린 리더에서 알려줘요. | 탭 컴포넌트를 구현할 때 `selected` 상태에 따라 `aria-selected` 속성이 자동 업데이트 됩니다. |

```jsx
<div role="tablist">
  <button role="tab" aria-selected="true">
    탭 1
  </button>
  <button role="tab" aria-selected="false">
    탭 2
  </button>
</div>
```

`Tab` 컴포넌트는 이러한 접근성 속성을 자동으로 지원해요. 특히 `selected` 상태에 따라 `aria-selected` 속성이 자동으로 업데이트되어 현재 선택된 탭을 스크린 리더 사용자에게 정확히 전달할 수 있어요.
`redBean` 속성이 `true`일 때, 업데이트 아이콘과 동시에 `title` 속성으로 "(업데이트 있음)"이 추가되어 스크린 리더 사용자에게도 정보를 알릴 수 있어요.

### 추가로 지원해야 하는 접근성

개발자가 추가로 접근성을 고려해야 할 때도 있어요.

#### 레이블이 별도로 있거나 의미 전달이 명확하지 않을 때

`Tab` 컴포넌트의 의미를 전달하는 텍스트가 없거나 별도의 요소에 있을 때, 또는 아이콘만 사용하는 등 의미를 전달하기 어려울 때는 `aria-label` 속성을 사용해서 `Tab` 컴포넌트의 역할을 설명해야 해요.

```jsx
<button role="tab" aria-selected="false" aria-label="설정">
  <SettingsIcon />
</button>
```

주의할 점은 `aria-label`을 작성할 때 "탭"이라는 요소 유형은 적지 않도록 해야 해요. 스크린 리더가 이미 "탭"이라고 읽어주기 때문에 중복된 정보가 제공되기 때문이에요.

## 인터페이스

**Type: TabProps**

```typescript
export interface TabProps {
  /**
   * `Tab`을 구성하는 하나 이상의 `Tab.Item` 컴포넌트를 받아요. `Tab.Item`은 각각의 탭을 나타내며, 여러 개의 `Tab.Item`을 배열로 전달할 수 있어요.
   */
  children: ReactNode;
  /**
   * 선택된 탭이 바뀔 때 실행되는 함수예요.
   */
  onChange: (index: number, key?: string | number) => void;
  /**
   * 사이즈에 따라 `Tab`의 높이와 텍스트 크기가 변경돼요.
   *
   * @default 'large'
   */
  size?: "large" | "small";
  /**
   * 이 값이 `true`일 때 각 아이템의 너비가 글자 수에 맞춰져요. 아이템의 전체 크기가 `Tab`의 컨테이너를 넘어가면 가로 스크롤이 생겨요. `false`라면 최대 4개의 아이템 사용을 권장해요.
   *
   * @default false
   */
  fluid?: boolean;
  /**
   * 이 값에 맞춰 탭의 간격을 변경해요. 예를 들어 이 값이 `4`라면, `4px`이 간격으로 적용돼요.
   */
  itemGap?: number;
  /**
   * 보조 기술(스크린 리더 등)이 인식할 수 있도록 요소의 역할을 설명하는 텍스트예요.
   */
  ariaLabel?: string;
}
```

**Type: TabItemProps**

```typescript
export interface TabItemProps {
  /**
   * 이 값이 `true`일 때 해당 `Tab.Item`이 선택된 상태로 표현돼요. 선택된 아이템을 바꾸려면 `Tab` 컴포넌트의 `onChange`에 상태를 바꾸는 함수를 전달해야 해요. (예: `setState`)
   */
  selected: boolean;
  /**
   * 이 값이 `true`일 때 `Tab.Item`의 우측 상단에 빨간 동그라미가 표시돼요. 중요한 알림이나 새로운 업데이트가 있음을 사용자에게 시각적으로 전달할 수 있어요.
   *
   * @default false
   */
  redBean?: boolean;

  // todo 문서에 반영할지 확인하기
  // focused?: boolean;
  // onSelectItem?: (width: number, offsetLeft: number) => void;
  // onResize?: (offsetLeft: number) => void;
}
```

---

# TableRow (/tds-mobile/components/table-row/)

# TableRow

`TableRow` 컴포넌트는 데이터를 간결하고 읽기 쉽게 좌우로 배치할 때 사용해요.  
주로 정보 제목과 내용을 나란히 배치해야 할 때 유용하며, 텍스트의 비율이나 정렬을 유연하게 조정할 수 있어요.

[Preview: TableRight]

## 사용법

`TableRow`는 세 가지 필수 속성을 가지고 있어요.

- `left`: 왼쪽에 배치될 요소를 받는 속성이에요. 문자열, 숫자, 또는 React 컴포넌트를 전달할 수 있어요.
- `right`: 오른쪽에 배치될 요소를 받는 속성이에요. 문자열, 숫자, 또는 React 컴포넌트를 전달할 수 있어요.
- `align`: 정렬 방향을 설정해요.

### 제목과 데이터를 양쪽 끝으로 배치하기

`align="space-between"` 속성을 사용하면 제목과 내용을 양쪽 끝으로 배치해 데이터를 분명히 구분할 수 있어요.  
주로 정보의 제목과 내용이 시각적으로 명확히 분리되어야 하는 경우 적합해요.

**Example: TableRight**

```tsx
<div></div>
```

### 제목과 데이터를 왼쪽으로 정렬하기

`align="left"` 속성을 사용하면 제목과 내용을 모두 한쪽으로 가까이 배치해요.  
제목과 내용이 같은 영역에 밀집되어 있어야 하거나, 공간이 제한된 상황에서 유용해요.

`leftRatio` 속성을 사용하면 좌측 영역의 비율을 조정해 균형 있는 레이아웃을 만들 수 있어요.
예를 들어, `leftRatio={30}`으로 설정하면 왼쪽 영역이 전체 너비의 30%를 차지하게 돼요.

**Example: TableLeft**

```tsx
<div></div>
```

## 인터페이스

**Type: TableRowProps**

```typescript
export interface TableRowProps {
  /**
   * 왼쪽에 배치되는 컴포넌트예요. 문자열, 숫자, 또는 React 컴포넌트를 전달할 수 있어요.
   */
  left: React.ReactNode;
  /**
   * 오른쪽에 배치되는 컴포넌트예요. 문자열, 숫자, 또는 React 컴포넌트를 전달할 수 있어요.
   */
  right: React.ReactNode;
  /**
   * 왼쪽 영역의 너비를 고정된 비율로 설정할 수 있어요.
   * 주로 `Left` 컴포넌트에서 사용해요.
   */
  leftRatio?: number;

  /**
   * 정렬 방향을 설정해요.
   * left: 왼쪽 정렬
   * space-between: 양끝 정렬
   */
  align: "left" | "space-between";
}
```

---

# Text Button (/tds-mobile/components/text-button/)

# Text Button

`TextButton` 컴포넌트는 사용자가 어떤 액션을 트리거하거나 이벤트를 실행할 때 사용해요.

[Preview: TextButton]

## 사용 예제

### 크기 조정하기

`TextButton` 컴포넌트의 크기는 `size` 속성을 사용해서 변경할 수 있어요. `xsmall`, `small`, `medium`, `large`, `xlarge`, `xxlarge` 값으로 텍스트 크기를 조정할 수 있어요.

**Example: Size**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <TextButton size="xsmall">텍스트 버튼</TextButton>
  <TextButton size="small">텍스트 버튼</TextButton>
  <TextButton size="medium">텍스트 버튼</TextButton>
  <TextButton size="large">텍스트 버튼</TextButton>
  <TextButton size="xlarge">텍스트 버튼</TextButton>
  <TextButton size="xxlarge">텍스트 버튼</TextButton>
</div>
```

### 형태 변경하기

`TextButton` 컴포넌트의 모양을 변경하려면 `variant` 속성을 사용하세요. 사용할 수 있는 값은 `arrow`와 `underline`이 있어요.

#### 화살표 추가하기

화살표 아이콘과 함께 사용하려면 `variant` 속성을 `arrow`로 설정하세요. 컴포넌트 오른쪽에 화살표가 추가돼요.

**Example: Arrow**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <TextButton size="medium" variant="arrow">
    텍스트 버튼
  </TextButton>
  <TextButton size="xlarge" variant="arrow">
    텍스트 버튼
  </TextButton>
  <TextButton size="xxlarge" variant="arrow">
    텍스트 버튼
  </TextButton>
</div>
```

#### 밑줄 긋기

`TextButton` 컴포넌트에 밑줄을 추가하려면 `variant` 속성을 `underline`으로 설정하세요.

**Example: Underline**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <TextButton size="medium" variant="underline">
    텍스트 버튼
  </TextButton>
  <TextButton size="xlarge" variant="underline">
    텍스트 버튼
  </TextButton>
  <TextButton size="xxlarge" variant="underline">
    텍스트 버튼
  </TextButton>
</div>
```

### 비활성화

텍스트 버튼을 비활성화하려면 `disabled` 속성을 사용하세요. 비활성화된 텍스트 버튼은 사용자가 클릭할 수 없고, 시각적으로도 비활성화된 상태임을 나타내요.

**Example: Disabled**

```tsx
<div style={{ display: "flex", alignItems: "center", gap: 8 }}>
  <TextButton size="medium" disabled>
    텍스트 버튼
  </TextButton>
  <TextButton size="xlarge" disabled>
    텍스트 버튼
  </TextButton>
  <TextButton size="xxlarge" disabled>
    텍스트 버튼
  </TextButton>
</div>
```

## 인터페이스

**Type: TextButtonProps**

```typescript
export interface TextButtonProps extends ParagraphTextProps {
  /**
   * `TextButton` 컴포넌트의 형태를 결정해요.
   * @default 'clear'
   */
  variant?: "arrow" | "underline" | "clear";
  /**
   * `TextButton` 컴포넌트의 비활성화 여부를 나타내요.
   */
  disabled?: boolean;
  /**
   * 텍스트 버튼의 사이즈를 결정해요.
   */
  size: "xsmall" | "small" | "medium" | "large" | "xlarge" | "xxlarge";
}
```

---

# SplitTextField (/tds-mobile/components/TextField/split-text-field/)

# SplitTextField

`SplitTextField` 컴포넌트는 입력 데이터를 여러 필드로 나누어 입력받을 때 사용돼요.
사용자가 각 부분에 초점을 맞추어 입력할 수 있어, 주민등록번호처럼 고정된 형식의 데이터를 정확히 입력하도록 도와줘요.
이를 사용하면 입력 흐름이 직관적이고 편리해지며, 사용자 오류를 줄일 수 있어요.

이 컴포넌트는 `RRN13`과 `RRNFirst7` 두 가지 컴포넌트를 제공해요. "RNN"은 Resident Registration Number를 의미하고, 뒤에 붙은 숫자는 자릿수를 의미해요.
`SplitTextField.RRN13` 컴포넌트는 주민등록번호 13자리를 입력받는 필드이고, `SplitTextField.RRNFirst7` 컴포넌트는 주민등록번호 앞 7자리를 입력받는 필드예요.

## 주민번호 13자리 사용하기

`SplitTextField.RRN13` 컴포넌트는 주민등록번호 13자리를 두 개의 입력 필드로 나누어 입력받을 수 있어요. 생년월일과 뒷자리를 분리하면, 입력 과정이 더 간단하고 명확해져요.
앞자리 6자리를 모두 입력하면 자동으로 뒷자리 입력 필드로 포커스가 이동하여 더욱 편리하게 입력할 수 있어요.

**Example: SplitTextFieldRRN13**

```tsx
<div></div>
```

## 주민번호 뒷자리 마스킹 사용하기

`mask` 속성을 사용하면 주민등록번호 뒷자리를 마스킹 처리할 수 있어요. 기본값은 `true`로, 사용자의 민감한 정보를 보호하면서도 입력값의 유효성을 유지할 수 있어요.
반면, `mask={false}`로 설정하면 주민등록번호의 뒷자리가 마스킹 처리되지 않고 그대로 표시돼요. 이는 사용자가 입력한 내용을 확인해야 하는 상황에서 유용할 수 있지만, 개인정보 보호 측면에서는 주의가 필요해요.

**Example: SplitTextFieldRRN13WithMask**

```tsx
<div></div>
```

## 주민번호 앞 7자리 사용하기

`SplitTextField.RRNFirst7` 컴포넌트는 주민등록번호의 앞 7자리(생년월일과 성별코드)만 입력받고 싶을 때 사용돼요. 예를 들어, 성인 인증처럼 기본적인 정보만 필요할 때 적합해요.

**Example: SplitTextFieldRRNFirst7**

```tsx
<div></div>
```

## 성별코드 마스킹 사용하기

`mask` 속성을 사용하면 주민등록번호 앞 7자리 중 성별코드만 마스킹 처리할 수 있어요. 기본값은 `false`로, 입력한 숫자가 그대로 표시돼요.
`mask={true}`로 설정하면 성별코드가 마스킹 처리되어 표시돼요. 이는 보안이 필요한 상황에서 유용하게 사용할 수 있어요.

**Example: SplitTextFieldRRNFirst7WithMask**

```tsx
<div></div>
```

## 분리된 입력 필드 설정하기

`SplitTextField` 컴포넌트의 각 필드는 `first`와 `second` 속성을 사용해 개별적으로 커스터마이즈할 수 있어요.
각 필드는 `TextField` 컴포넌트의 `placeholder`, `disabled` 등의 주요 속성들을 사용할 수 있어요.

- `first`: 첫 번째 입력 필드의 속성을 설정해요. 예를 들어 생년월일 입력 시 'YYMMDD' 형식의 `placeholder`를 설정할 수 있어요.
- `second`: 두 번째 입력 필드의 속성을 설정해요. first 필드와 다른 형식의 `placeholder`를 설정할 수 있어요.

**Example: SplitTextFieldDefault**

```tsx
<div></div>
```

## 인터페이스

**Type: SplitTextFieldProps**

```typescript
export interface SplitTextFieldProps {
  /**
   * 텍스트 필드의 형태를 선택해요.
   *
   * - `box`: 기본 형태의 사각형 스타일
   * - `line`: 입력 필드 아래에 선만 표시되는 스타일
   * - `big`: 텍스트가 강조되는 큰 스타일
   * - `hero`: 사용자의 시선을 끌기에 좋은 대형 스타일
   */
  variant: "box" | "line" | "big" | "hero";
  /**
   * 텍스트 필드의 위쪽 라벨이에요.
   * @default '주민등록번호'
   */
  label: string;
  /**
   * 텍스트 필드의 라벨 표시 옵션을 설정해요.
   * `variant`가 'box'일 때 'sustain', 그렇지 않으면 'appear'이 기본값이에요.
   *
   * - `appear`: value가 있을 때만 label이 보여요.
   * - `sustain`: 항상 label이 보여요.
   */
  labelOption: "appear" | "sustain";
  /**
   * 텍스트 필드의 아래쪽 도움말이에요.
   */
  help?: React.ReactNode;
  /**
   * 텍스트 필드의 위쪽 패딩이에요.
   */
  paddingTop?: number | string;
  /**
   * 텍스트 필드의 아래쪽 패딩이에요.
   */
  paddingBottom?: number | string;
  /**
   * 에러 상태 여부를 나타내요.
   * @default false
   */
  hasError?: boolean;
  /**
   * 첫 번째 텍스트 필드의 속성을 설정해요.
   */
  first?: "TextFieldPublicProps";
  /**
   * 두 번째 텍스트 필드의 속성을 설정해요.
   */
  second?: "TextFieldPublicProps";
  /**
   * 텍스트 필드의 포커스 여부를 나타내요.
   */
  focused?: boolean;
}
```

**Type: RRN13TextFieldProps**

```typescript
export interface RRN13TextFieldProps extends SplitTextFieldProps {
  /**
   * `RRN13TextField` 컴포넌트 주민번호 뒷자리의 마스킹 여부를 나타내요.
   * @default true
   */
  mask?: boolean;
}
```

**Type: RRNFirst7TextFieldProps**

```typescript
export interface RRNFirst7TextFieldProps extends SplitTextFieldProps {
  /**
   * `RRNFirst7TextField` 컴포넌트 주민번호 뒷자리의 마스킹 여부를 나타내요.
   * @default false
   */
  mask?: boolean;
}
```

---

# TextArea (/tds-mobile/components/TextField/text-area/)

# TextArea

`TextArea` 컴포넌트는 여러 줄의 텍스트 입력을 받을 수 있는 컴포넌트로, 피드백 작성, 주소 입력, 메모와 같이 긴 텍스트 데이터를 처리할 때 사용돼요.
`height` 속성을 사용해 입력 영역의 높이를 조정할 수 있어 사용자가 더 편리하게 긴 내용을 작성할 수 있어요.
이 컴포넌트를 사용하면 사용자에게 넉넉한 입력 공간을 제공하고, 긴 텍스트를 효율적으로 입력하고 편집할 수 있는 환경을 만들어줘요.

## 높이가 고정된 텍스트 영역 사용하기

`height` 속성을 사용해 입력 영역의 높이를 고정할 수 있어요. 이는 특정 높이의 입력 영역이 필요한 경우에 유용해요.
예를 들어, 짧은 리뷰나 간단한 메모를 작성할 때는 작은 높이로, 긴 피드백이나 상세한 설명을 작성할 때는 큰 높이로 설정할 수 있어요.
이렇게 고정된 높이를 사용하면 레이아웃이 일관되게 유지되어 UI의 안정성을 높일 수 있어요.

**Example: TextAreaHeight**

```tsx

```

## 높이가 자동으로 조정되는 텍스트 영역 사용하기

텍스트 입력 시 내용의 양에 따라 입력 영역의 높이가 자동으로 늘어나요. 이는 사용자가 긴 내용을 입력할 때 스크롤 없이도 전체 내용을 한눈에 볼 수 있게 해줘요.
`minHeight` 속성으로 입력 영역의 최소 높이를 지정할 수 있어 너무 작아지는 것을 방지할 수 있어요.

**Example: TextAreaAutoHeight**

```tsx

```

## 인터페이스

**Type: TextAreaProps**

```typescript
export interface TextAreaProps extends Omit<
  TextFieldPublicProps,
  "prefix" | "suffix" | "right"
> {
  /**
   * `TextArea` 컴포넌트의 최소 높이를 설정해요.
   */
  minHeight?: number | string;
  /**
   * `TextArea` 컴포넌트의 높이를 설정해요.
   */
  height?: number | string;
}
```

---

# TextField (/tds-mobile/components/TextField/text-field/)

# TextField

`TextField` 컴포넌트는 사용자로부터 입력을 받는 가장 기본적인 UI 요소로, 다양한 디자인 옵션과 속성을 제공하여 일반 텍스트 입력부터 비밀번호 입력까지 다양한 상황에 적합하게 사용할 수 있어요.

`label`과 `placeholder`는 사용자가 입력 필드의 목적을 이해하도록 도와주고 `help`는 추가적인 안내 메시지를 제공해 입력 과정을 더 명확하게 해줘요.
이 컴포넌트는 다양한 상태와 옵션을 제공해서 어떤 사용 환경에서도 유연하게 동작해요. 예를 들어, `disabled` 상태를 사용해 비활성화된 입력 필드를 제공하거나, `hasError` 속성을 활용해 사용자가 잘못된 값을 입력했을 때 실수를 시각적으로 알릴 수 있어요.

[Preview: Basic]

## 형태 변경하기

`variant` 속성을 사용하면 입력 필드의 디자인을 변경할 수 있어요. 사용 가능한 형태는 `box`, `line`, `big`, `hero`가 있어요.

- `box`: 기본 형태의 사각형 스타일로, 명확하고 간결해요.
- `line`: 입력 필드 아래에 선만 표시되는 스타일로, 깔끔한 인상을 줘요.
- `big`: 큰 글씨로 눈에 띄게 만든 스타일로, 사용자가 꼭 써야 하는 내용을 알려줘요.
- `hero`: 사용자의 시선을 끌기에 좋은 대형 스타일이에요.

**Example: TextFieldDefault**

```tsx
<div></div>
```

### 에러 상태 사용하기

`hasError` 속성을 사용하면 입력 필드가 에러 상태로 표시돼요. 사용자가 입력한 값이 유효하지 않을 때 시각적으로 알려줄 수 있어요. `hasError`와 `help` 속성을 함께 사용하면 사용자에게 더 명확한 피드백을 제공할 수 있어요.

예를 들어, 글자 수 제한이 있는 입력 필드에서 3글자 이상 입력했을 때 에러 상태를 표시하고 도움말로 '3글자 미만으로 입력해주세요'라는 메시지를 보여주면, 사용자가 바로 문제를 인지하고 수정할 수 있어요. 이런 즉각적인 피드백은 사용자 경험을 개선하고 입력 오류를 효과적으로 줄일 수 있어요.

**Example: TextFieldError**

```tsx
function TextFieldError() {
  const [boxValue, setBoxValue] = React.useState("");
  const [lineValue, setLineValue] = React.useState("");

  const errorMessage = "3글자 미만으로 입력해주세요.";

  const handleError = (value: string) => {
    return value.length > 2;
  };

  return (
    <div>
      <TextField
        variant="box"
        label="에러 상태 텍스트 필드"
        help={handleError(boxValue) ? errorMessage : null}
        labelOption="sustain"
        placeholder="3글자 이상 입력하면 에러 상태가 적용돼요."
        hasError={handleError(boxValue)}
        value={boxValue}
        onChange={(e) => setBoxValue(e.target.value)}
      />
      <TextField
        variant="line"
        label="에러 상태 텍스트 필드"
        help={handleError(lineValue) ? errorMessage : null}
        labelOption="sustain"
        placeholder="3글자 이상 입력하면 에러 상태가 적용돼요."
        hasError={handleError(lineValue)}
        value={lineValue}
        onChange={(e) => setLineValue(e.target.value)}
      />
    </div>
  );
}
```

### 비활성화 상태 사용하기

`disabled` 속성을 사용하면 입력 필드가 비활성화돼요. 비활성화된 필드는 사용자와의 상호작용이 제한되고 읽기 전용이나 입력이 필요하지 않은 상황에서 사용돼요.
예를 들어, 서버 응답 대기 중 데이터를 잠시 수정하지 못하게 하거나, 사용자가 특정 조건을 충족해야 활성화할 수 있는 입력 필드에서 활용할 수 있어요.
비활성화 상태는 시각적으로도 구분돼 입력이 불가능하다는 점을 명확히 전달할 수 있어요. 이렇게 불필요한 입력을 방지하면 UI의 명확성을 높일 수 있어요.

**Example: TextFieldDisabled**

```tsx
<div></div>
```

### 라벨 표시 방식 변경하기

`labelOption` 속성은 라벨의 표시 방식을 설정해요. 사용 가능한 방식은 `appear`과 `sustain`이에요.

- `sustain`: 항상 라벨이 보여 사용자가 입력 필드의 목적을 항상 명확히 알 수 있도록 하고 특히 입력 필드가 여러 개일 때 혼동을 줄이는 데 유용해요.
- `appear`: 값이 있을 때만 라벨이 보여 입력 필드가 깔끔하게 보이도록 하고 사용자가 입력을 시작할 때만 라벨이 나타나도록 해서 시각적 혼잡을 줄일 수 있어요.

**Example: TextFieldLabelOption**

```tsx
<div></div>
```

### 접두사, 접미사 사용하기

`prefix`와 `suffix` 속성을 사용하면 입력 필드의 앞뒤에 텍스트나 기호를 추가할 수 있어요.
금액, 단위와 같은 데이터를 입력받을 때 사용자에게 입력 형식을 직관적으로 보여줄 수 있어요. 예를 들어, `₩`를 접두사로 추가하면 금액 입력임을 즉시 알 수 있고, `kg`를 접미사로 추가하면 입력 데이터의 단위를 명확히 알 수 있어요.

**Example: TextFieldPrefixSuffix**

```tsx
<div></div>
```

### 오른쪽 영역에 컴포넌트 추가하기

`right` 속성을 사용하면 입력 필드 오른쪽에 사용자 액션을 위한 버튼이나 추가 정보를 배치할 수 있어요.
예를 들어, 검색 필드에 검색 버튼을 추가하면 사용자가 입력값을 바로 검색할 수 있어요. 또, 유효성 검사 상태를 아이콘으로 표시해 사용자에게 입력값의 유효 여부를 시각적으로 알려줄 수도 있어요.

**Example: TextFieldRightCustom**

```tsx
<div>
  <TextField
    variant="box"
    label="오른쪽 컴포넌트"
    labelOption="sustain"
    help="오른쪽 영역에 컴포넌트를 넣을 수 있어요."
    placeholder="Placeholder"
    right={<Button size="small">버튼</Button>}
  />
  <TextField
    variant="line"
    label="오른쪽 컴포넌트"
    labelOption="sustain"
    help="오른쪽 영역에 컴포넌트를 넣을 수 있어요."
    placeholder="Placeholder"
    right={<Button size="small">버튼</Button>}
  />
</div>
```

## 클리어 버튼 사용하기

`TextField.Clearable` 컴포넌트는 입력 필드에 클리어 버튼을 제공하는 컴포넌트예요.
사용자는 초기화 버튼을 클릭해 입력 내용을 한 번에 지울 수 있어요. 이 과정에서 `onClear` 이벤트를 활용해 필터링된 목록을 초기 상태로 되돌리거나 최근 검색어 목록을 업데이트하는 등의 추가 작업을 수행할 수 있어요.
이 컴포넌트는 검색창이나 폼 필드에서 잘못된 입력을 빠르게 수정하거나 재입력을 유도하고 싶을 때 적합해요.
클리어 버튼을 사용하면 사용자가 입력 내용을 쉽게 정리할 수 있어 폼 입력이나 검색 경험을 크게 개선할 수 있어요.

**Example: TextFieldClearable**

```tsx
<div>
  <TextField.Clearable
    variant="box"
    label="클리어 가능한 텍스트 필드"
    labelOption="sustain"
    help="값을 입력 후, 오른쪽 clear 버튼을 눌러보세요. onClear가 실행돼요."
    placeholder="Placeholder"
    onClear={() => {
      window.alert("clear");
    }}
  />
  <TextField.Clearable
    variant="line"
    label="클리어 가능한 텍스트 필드"
    labelOption="sustain"
    help="값을 입력 후, 오른쪽 clear 버튼을 눌러보세요. onClear가 실행돼요."
    placeholder="Placeholder"
    onClear={() => {
      window.alert("clear");
    }}
  />
</div>
```

## 비밀번호 형태로 사용하기

`TextField.Password` 컴포넌트는 비밀번호와 같은 민감한 정보를 안전하게 입력받는 컴포넌트예요.
기본적으로 입력값이 마스킹되어 있어 다른 사람이 내용을 확인할 수 없도록 보호하고, 필요에 따라 입력값을 표시하거나 숨길 수 있는 버튼도 제공해요.
비밀번호 입력 중 실수를 줄이고 사용자가 내용을 검토할 수 있는 선택지를 제공하기 때문에, 보안과 편리함을 모두 충족할 수 있어요.
이 컴포넌트를 사용하면 사용자가 안심하고 중요한 정보를 입력할 수 있는 환경을 조성할 수 있어요.

**Example: TextFieldPassword**

```tsx
<div>
  <TextField.Password
    variant="box"
    label="비밀번호 입력 필드"
    labelOption="sustain"
    help="콘솔창을 통해 visible 상태를 확인해보세요."
    placeholder="Placeholder"
    onVisibilityChange={(visible: boolean) => {
      alert(`visible: ${visible}`);
    }}
  />
  <TextField.Password
    variant="line"
    label="비밀번호 입력 필드"
    labelOption="sustain"
    help="콘솔창을 통해 visible 상태를 확인해보세요."
    placeholder="Placeholder"
    onVisibilityChange={(visible: boolean) => {
      alert(`visible: ${visible}`);
    }}
  />
</div>
```

## 버튼으로 사용하기

`TextField.Button` 컴포넌트는 입력 필드와 유사한 형태를 가지면서도 클릭 가능한 버튼으로, 사용자가 특정 작업을 수행할 수 있도록 돕는 컴포넌트예요.
기본적으로 입력 필드처럼 보이지만, 실제로는 `<button>` 엘리먼트를 사용하여 사용자가 값을 선택하거나 작업을 트리거할 수 있는 인터페이스를 제공해요.
이 컴포넌트는 입력 필드와 비슷한 UI를 유지하면서도 클릭 가능한 액션을 제공하여, 사용자가 직관적으로 작업을 수행할 수 있도록 해줘요.

**Example: TextFieldButton**

```tsx
<div>
  <TextField.Button
    variant="box"
    label="버튼이 있는 텍스트 필드"
    labelOption="sustain"
    help="입력 필드를 눌러보세요."
    placeholder="Button"
    onClick={() => window.alert("click")}
  />
  <TextField.Button
    variant="line"
    label="버튼이 있는 텍스트 필드"
    labelOption="sustain"
    help="입력 필드를 눌러보세요."
    placeholder="Button"
    onClick={() => window.alert("click")}
  />
</div>
```

## 인터페이스

**Type: TextFieldPublicProps**

```typescript
export interface TextFieldPublicProps {
  /**
   * 텍스트 필드의 비활성화 여부를 나타내요.
   *
   * @default false
   */
  disabled?: boolean;
  /**
   * 텍스트 필드의 앞에 위치할 문자열을 설정해요.
   */
  prefix?: string;
  /**
   * 텍스트 필드의 뒤에 위치할 문자열을 설정해요.
   */
  suffix?: string;
  /**
   * 텍스트 필드의 오른쪽에 위치할 컴포넌트를 설정해요.
   */
  right?: React.ReactNode;
  /**
   * 텍스트 필드의 플레이스홀더를 설정해요.
   */
  placeholder?: string;
  /**
   * 특정 형식으로 변환하기 위한 설정이에요.
   * @type {{
   *   transform: (value: string) => string;
   *   reset: (formattedValue: string) => string;
   * }}
   *
   * 금액, 휴대폰번호 등 특정 형식으로 변환해야 할 떼 사용해요.
   * transform: 입력값(value) => 변환된 값
   * reset: 변환된 값 => 입력값(value)
   *
   * @example 금액
   * format={{
   *  transform: value => commaizeNumber(value)
   *  reset: formattedValue => decommaizeNumber(formattedValue)
   * }}
   */
  format?: {
    transform: (value: string) => string;
    reset?: (formattedValue: string) => string;
  };
}
```

**Type: TextFieldProps**

```typescript
export interface TextFieldProps extends TextFieldPublicProps {
  /**
   * 텍스트 필드의 형태를 선택해요.
   *
   * - `box`: 기본 형태의 사각형 스타일
   * - `line`: 입력 필드 아래에 선만 표시되는 스타일
   * - `big`: 텍스트가 강조되는 큰 스타일
   * - `hero`: 사용자의 시선을 끌기에 좋은 대형 스타일
   */
  variant: "box" | "line" | "big" | "hero";
  /**
   * 텍스트 필드의 위쪽 라벨이에요.
   */
  label?: string;
  /**
   * 라벨 표시 옵션을 설정해요.
   *
   * - `appear`: value가 있을 때만 label이 보여요.
   * - `sustain`: 항상 label이 보여요.
   * @default appear
   */
  labelOption?: "appear" | "sustain";
  /**
   * 텍스트 필드의 아래쪽 도움말이에요.
   */
  help?: React.ReactNode;

  /**
   * 에러 상태 여부를 나타내요.
   * @default false
   */
  hasError?: boolean;
  /**
   * 텍스트 필드의 위쪽 패딩이에요.
   */
  paddingTop?: number | string;
  /**
   * 텍스트 필드의 아래쪽 패딩이에요.
   */
  paddingBottom?: number | string;
  /**
   * 제어된 입력 값이에요.
   */
  value?: string | number;
  /**
   * 기본 입력 값이에요.
   */
  defaultValue?: string;
  /**
   * 포커스 이벤트 핸들러예요.
   * 이 핸들러는 입력 필드가 포커스를 받을 때 호출돼요.
   */
  onFocus?: (event: FocusEvent<HTMLInputElement>) => void;
  /**
   * 블러 이벤트 핸들러예요.
   * 이 핸들러는 입력 필드가 포커스를 잃을 때 호출돼요
   */
  onBlur?: (event: FocusEvent<HTMLInputElement>) => void;
  /**
   * 변경 이벤트 핸들러예요.
   * 이 핸들러는 입력 필드의 값이 변경될 때마다 호출돼요.
   */
  onChange?: (event: ChangeEvent<HTMLInputElement>) => void;
}
```

**Type: TextFieldButtonProps**

```typescript
export interface TextFieldButtonProps extends TextFieldPublicProps {
  /**
   * `TextFieldButton` 컴포넌트의 오른쪽에 위치할 컴포넌트예요.
   * @default
   */
  right?: React.ReactNode;
}
```

**Type: TextFieldClearableProps**

```typescript
export interface TextFieldClearableProps extends Omit<TextFieldProps, "right"> {
  /**
   * `TextFieldClearable` 컴포넌트의 클리어 버튼을 클릭하면 호출되는 함수예요.
   */
  onClear?: () => void;
}
```

**Type: TextFieldPasswordProps**

```typescript
export interface TextFieldPasswordProps extends Omit<TextFieldProps, "right"> {
  /**
   * 비밀번호 표시 여부를 변경하면 호출되는 함수예요.
   */
  onVisibilityChange?: (visible: boolean) => void;
}
```

---

# Toast (/tds-mobile/components/toast/)

# Toast

`Toast` 컴포넌트는 사용자가 어떤 작업을 완료했거나, 이벤트가 발생했을 때 그 내용에 대해 알리거나 피드백을 하기 위해 사용해요. 이 컴포넌트를 사용하면 메시지가 화면 상단이나 하단에 짧은 시간 동안 표시된 뒤 자동으로 사라져요.

[Preview: Basic]

## 사용법

`Toast` 컴포넌트는 `overlay-extension`을 통해 사용하는 것을 권장해요. 다만 이 문서에서는 독립적으로 `Toast` 컴포넌트를 이해할 수 있도록 도와드려요.

### 토스트 노출 위치 지정하기

가장 기본적인 형태의 토스트 메시지를 표시할 수 있어요. `Toast` 컴포넌트의 위치는 `position` 속성을 사용해 설정할 수 있어요. 사용할 수 있는 값은 `bottom`, `top`이에요.

**Example: BasicToasts**

```tsx
/** 기본 토스트 (상단) */
function BasicToasts() {
  const [openTop, setOpenTop] = React.useState(false);
  const [openBottom, setOpenBottom] = React.useState(false);

  return (
    <div style={{ display: "flex", flexDirection: "row", gap: "12px" }}>
      <Button onClick={() => setOpenTop(true)}>상단 토스트 열기</Button>
      <Toast
        position="top"
        open={openTop}
        text="상단 토스트 메시지이에요"
        duration={3000}
        onClose={() => setOpenTop(false)}
      />
      <Button onClick={() => setOpenBottom(true)}>하단 토스트 열기</Button>
      <Toast
        position="bottom"
        open={openBottom}
        text="하단 토스트 메시지이에요"
        duration={3000}
        onClose={() => setOpenBottom(false)}
      />
    </div>
  );
}
```

### 아이콘 추가하기

`leftAddon` 속성을 사용해서 토스트 메시지 왼쪽에 아이콘을 추가할 수 있어요. 성공, 경고, 에러 등 메시지의 성격을 시각적으로 전달할 때 유용해요.

**Example: ToastWithIcon**

```tsx
/** 아이콘이 있는 토스트 */
function ToastWithIcon() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>아이콘 토스트 열기</Button>
      }
        duration={3000}
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

### 버튼 추가하기

하단 `Toast` 컴포넌트에서는 `button` 속성을 사용하여 액션 버튼을 추가할 수 있어요. 사용자가 `Toast` 컴포넌트에 대해 즉각적인 액션을 취할 수 있게 해줘요.

**Example: ToastWithButton**

```tsx
/** 버튼이 있는 토스트 (하단 전용) */
function ToastWithButton() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>버튼 토스트 열기</Button>
      <Toast
        position="bottom"
        open={open}
        text="버튼이 포함된 토스트이에요"
        button={
          <Toast.Button onClick={() => alert("clicked")}>확인</Toast.Button>
        }
        duration={3000}
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

### CTA 위에 표시하기

`higherThanCTA` 속성을 사용하면 하단 고정 CTA 버튼보다 위에 토스트를 표시할 수 있어요. 주요 액션 버튼을 가리지 않으면서도 알림을 표시할 수 있어요.

**Example: ToastAboveCTA**

```tsx
/** CTA 위에 표시되는 토스트 */
function ToastAboveCTA() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>CTA 위 토스트 열기</Button>
      <Toast
        position="bottom"
        open={open}
        text="CTA 버튼 위에 표시되는 토스트이에요"
        higherThanCTA
        duration={3000}
        onClose={() => setOpen(false)}
      />
      {open ? (
        <FixedBottomCTA>CTA 버튼</FixedBottomCTA>
      ) : (
        <div style={{ height: "110px" }} />
      )}
    </>
  );
}
```

### 로티 애니메이션 사용하기

`leftAddon`에 `Toast.Lottie` 컴포넌트를 사용하여 로티 애니메이션을 표시할 수 있어요.

**Example: ToastWithLottie**

```tsx
/** 로티 애니메이션이 있는 토스트 */
function ToastWithLottie() {
  const [open, setOpen] = React.useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>로티 토스트 열기</Button>
      }
        duration={3000}
        onClose={() => setOpen(false)}
      />
    </>
  );
}
```

## 접근성

`Toast` 컴포넌트는 다음과 같은 접근성 기능을 제공해요:

- `aria-live` 속성을 통해 스크린 리더 사용자에게 적절한 알림을 제공해요.
  - `assertive`: 즉시 읽기 (중요한 알림에 사용)
  - `polite`: 현재 읽고 있는 내용을 마친 후 읽기 (일반적인 알림에 사용)

## 인터페이스

**Type: ToastProps**

```typescript
export interface ToastProps {
  /**
   * `Toast` 컴포넌트의 열림 상태를 제어해요.
   */
  open: boolean;

  /**
   * `Toast` 컴포넌트의 위치를 결정해요.
   */
  position: "top" | "bottom";

  /**
   * `Toast` 컴포넌트에 표시할 메시지에요.
   */
  text: string;

  /**
   * `Toast` 컴포넌트의 왼쪽에 표시할 아이콘이나 로티 애니메이션이에요.
   *
   * `Toast.Icon`, `Toast.Lottie`를 사용할 수 있어요.
   */
  leftAddon?: ReactNode;

  /**
   * `Toast` 컴포넌트의 버튼이에요.`position: "bottom"`에서만 사용할 수 있어요.
   */
  button?: ReactNode;

  /**
   * `Toast` 컴포넌트가 자동으로 닫히는 시간(ms)이에요.
   *
   * 기본은 3000이고, 버튼을 사용했다면 5000이에요.
   *
   * @default 3000
   */
  duration?: number;

  /**
   * `Toast` 컴포넌트가 닫히기 시작할 때 호출되는 콜백 함수에요.
   *
   * 아래와 같은 상황에서 사용할 수 있어요:
   * - `duration` 시간이 지나서 자동으로 닫힐 때
   * - 사용자가 `Toast` 컴포넌트를 드래그해서 닫을 때
   * - 수동으로 `open` 값을 `false`로 변경할 때
   */
  onClose?: () => void;

  /**
   * `Toast` 컴포넌트가 완전히 사라지고 애니메이션이 끝난 후에 호출되는 콜백 함수에요.
   *
   * 아래와 같은 상황에서 사용할 수 있어요:
   * - `Toast` 컴포넌트가 완전히 사라진 후 다음 작업을 진행해야 할 때
   */
  onExited?: () => void;

  /**
   * `Toast` 컴포넌트가 `FixedBottomCTA`보다 위에 표시될지 결정해요.
   *
   * `position: bottom`일 때만 사용할 수 있어요.
   *
   * @default false
   */
  higherThanCTA?: boolean;

  /**
   * `Toast` 컴포넌트가 나타났을 때, 스크린리더가 `Toast` 컴포넌트의 메시지를 읽는 우선순위를 결정해요.
   *
   * 기본 값은 `polite`이고, `assertive`로 설정하면 즉시 읽기가 돼요.
   *
   * - `assertive`: 즉시 읽기
   * - `polite`: 현재 읽고 있는 메시지를 모두 읽은 뒤 읽기
   *
   * @default 'polite'
   */
  "aria-live"?: "assertive" | "polite";
}
```

**Type: ToastButtonProps**

```typescript
export interface ToastButtonProps {
  /**
   * 버튼에 표시할 텍스트에요.
   */
  children: string;

  /**
   * 버튼 클릭 시 호출되는 콜백 함수에요.
   */
  onClick?: () => void;
}
```

**Type: ToastIconProps**

```typescript
export interface ToastIconProps {
  /**
   * 아이콘의 이름이에요.
   */
  name: string;

  /**
   * 아이콘의 종류에요.
   */
  icon: string;

  /**
   * 아이콘의 크기를 조절할 수 있어요.
   *
   * @default { width: 24, height: 24 }
   */
  frameShape?: "FrameShapeType";
}
```

**Type: ToastLottieProps**

```typescript
export interface ToastLottieProps {
  /**
   * 로티 애니메이션의 소스 경로에요.
   */
  src: string;

  /**
   * 로티 애니메이션의 크기를 조절할 수 있어요.
   *
   * @default { width: 24, height: 24 }
   */
  frameShape?: "FrameShapeType";
}
```

**Type: FrameShapeType**

```typescript
export interface FrameShapeType {
  /**
   * 프레임의 너비를 지정해요.
   */
  width?: string | number;

  /**
   * 프레임의 높이를 지정해요.
   */
  height?: string | number;

  /**
   * 프레임의 모서리 둥글기를 지정해요.
   */
  radius?: string | number;

  /**
   * 프레임의 액세서리 영역 설정이에요.
   */
  acc?: "FrameAccShapeType";

  /**
   * 프레임 뒤에 겹침 효과를 설정해요.
   *
   * 여러 개의 항목이 합쳐졌음을 표현할 때 사용해요.
   */
  overlap?: "FrameOverlapShapeType";
}
```

---

# Tooltip (/tds-mobile/components/tooltip/)

# Tooltip

`Tooltip` 컴포넌트는 사용자가 특정 요소에 포커스할 때 추가적인 정보를 제공하기 위해 사용해요. 보통 아이콘이나 버튼과 같은 작은 UI 요소 위에 `Tooltip` 컴포넌트를 이용해 보조적인 내용을 전달해요.

[Preview: Controlled]

## 사용법

### 상태

`Tooltip` 컴포넌트는 열림과 닫힘 상태를 외부에서 관리하는 방식, 내부에서 관리하는 방식 모두 사용 가능해요.

#### 상태를 외부에서 관리하기

`Tooltip` 컴포넌트의 열림과 닫힘 상태를 외부에서 관리하려면, `open` 속성에 메시지 열림 여부 상태를 설정하세요.

**Example: Controlled**

```tsx
function Controlled() {
  const [isOpen, setIsOpen] = React.useState(false);

  return (
    <div style={{ paddingBottom: 80 }}>
      <Tooltip message={"툴팁입니다."} open={isOpen}>
        <Button
          onClick={() => {
            setIsOpen((prev) => !prev);
          }}
        >
          Click Me
        </Button>
      </Tooltip>
    </div>
  );
}
```

#### 상태를 내부에서 관리하기

`open` 속성을 주지 않으면 `Tooltip` 컴포넌트 내부에서 열림과 닫힘 상태가 관리돼요. 이때 `defaultOpen` 속성을 통해 초기 값을 지정할 수 있어요.
그리고 아래 속성들을 통해 `Tooltip` 컴포넌트 내부에서 스스로 열림과 닫힘 상태가 변경되게 할 수 있어요.

- `openOnHover`: `true`일 경우, `Tooltip` 컴포넌트 위에 마우스 포인터를 올리면 메시지가 열려요. 마우스 포인터를 내리면 메시지가 닫혀요.
- `openOnFocus`: `true`일 경우, `Tooltip` 컴포넌트가 포커스 되면 메시지가 열려요. 포커스가 되지 않으면 메시지가 닫혀요.
- `dismissible`: `true`일 경우, `Tooltip` 컴포넌트 외부를 클릭하거나 `escape` 키를 누르면 메시지가 닫혀요.

**Example: Uncontrolled**

````tsx
<div style={{ display: 'flex', gap: 10, paddingBottom: 80 }}>
  <Tooltip message={'툴팁입니다.'} openOnHover>
    <Button>Hover Me</Button>
  </Tooltip>
  <Tooltip message={'툴팁입니다.'} openOnFocus>
    <Button>Focus Me</Button>
  </Tooltip>
  <Tooltip message={'툴팁입니다.'} defaultOpen openOnFocus openOnHover dismissible>
    <Button>Default Open</Button>
  </Tooltip>
</div>
```{' '}

### 크기 정하기

`Tooltip` 컴포넌트의 크기를 정하려면 `size` 속성을 사용하세요. 가능한 값으로는 `small`, `medium`, `large`가 있고 `medium`이 기본값이에요.

**Example: Size**

```tsx
<div style={{ display: 'flex', gap: 10, paddingBottom: 80 }}>
  <Tooltip message={'툴팁입니다.'} defaultOpen openOnHover size="small">
    <Button>Small</Button>
  </Tooltip>
  <Tooltip message={'툴팁입니다.'} defaultOpen openOnHover size="medium">
    <Button>Medium</Button>
  </Tooltip>
  <Tooltip message={'툴팁입니다.'} defaultOpen openOnHover size="large">
    <Button>Large</Button>
  </Tooltip>
</div>
````

### 메시지

`Tooltip` 컴포넌트의 메시지 내용은 `message` 속성으로 설정해요.

#### 메시지 정렬하기

`Tooltip` 컴포넌트의 메시지를 정렬 방식을 정하려면 `messageAlign` 속성을 사용하세요. `Tooltip` 컴포넌트의 넓이가 고정되어있어야 해요.

**Example: MessageAlign**

```tsx
<div style={{ display: "flex", gap: 50, paddingBottom: 80 }}>
  <Tooltip
    message={"툴팁입니다."}
    messageAlign="left"
    defaultOpen
    openOnHover
    style={{ width: 150 }}
  >
    <Button>Left</Button>
  </Tooltip>
  <Tooltip
    message={"툴팁입니다."}
    messageAlign="center"
    defaultOpen
    openOnHover
    style={{ width: 150 }}
  >
    <Button>Center</Button>
  </Tooltip>
  <Tooltip
    message={"툴팁입니다."}
    messageAlign="right"
    defaultOpen
    openOnHover
    style={{ width: 150 }}
  >
    <Button>Right</Button>
  </Tooltip>
</div>
```

### 위치

#### 상하 위치 정하기

`Tooltip` 컴포넌트가 `Tooltip` 컴포넌트의 트리거로부터 어떤 위치에 메시지를 표시할지를 정하려면 `placement` 속성을 사용하세요. 가능한 값으로는 `top`, `bottom`이 있고, `bottom`이 기본값이에요.

**Example: Placement**

```tsx
<div style={{ display: "flex", gap: 10, padding: 80 }}>
  <Tooltip message={"툴팁입니다."} placement="top" defaultOpen openOnHover>
    <Button>Top</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} placement="bottom" defaultOpen openOnHover>
    <Button>Bottom</Button>
  </Tooltip>
</div>
```

#### 위치 자동 조정하기

`Tooltip` 컴포넌트가 시야에서 자동으로 벗어날 때, `Tooltip` 컴포넌트가 가려진 반대 방향으로 위치가 조정되게 하려면, `autoFlip` 속성을 사용하세요.

**Example: AutoFlip**

```tsx
<div style={{ padding: 80 }}>
  <Tooltip message={"툴팁입니다."} defaultOpen autoFlip>
    <Button>스크롤하여 확인해보세요</Button>
  </Tooltip>
</div>
```

#### 트리거 대상까지의 거리 정하기

`Tooltip` 컴포넌트와 `Tooltip` 컴포넌트 트리거 사이의 거리를 정하려면 `offset` 속성을 사용하세요. 기본값은 `Tooltip` 컴포넌트의 화살표와 `size` 속성에 따라 결정돼요.
임의의 값을 지정한다면 화살표의 사이즈를 고려하여 설정해주세요.

**Example: Offset**

```tsx
<div style={{ display: "flex", gap: 10, paddingBottom: 80 }}>
  <Tooltip message={"툴팁입니다."} offset={0} defaultOpen openOnHover>
    <Button>Offset 0</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} offset={15} defaultOpen openOnHover>
    <Button>Offset 15</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} offset={30} defaultOpen openOnHover>
    <Button>Offset 30</Button>
  </Tooltip>
</div>
```

### 화살표

#### 화살표 형태 정하기

메시지가 `Tooltip` 컴포넌트를 가리키는 화살표의 형태를 변경하려면 `clipToEnd` 속성을 활용하세요.
`none`일 경우 기본 형태를 유지하고, `left`, `right`인 경우 각각 화살표의 왼쪽, 오른쪽을 남겨요.

**Example: ClipToEnd**

```tsx
<div style={{ display: "flex", gap: 10, paddingBottom: 80 }}>
  <Tooltip message={"툴팁입니다."} clipToEnd="none" defaultOpen openOnHover>
    <Button>none</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} clipToEnd="left" defaultOpen openOnHover>
    <Button>left</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} clipToEnd="right" defaultOpen openOnHover>
    <Button>right</Button>
  </Tooltip>
</div>
```

#### 화살표의 위치 정하기

`Tooltip` 컴포넌트의 화살표 위치를 정하려면 `anchorPositionByRatio` 속성을 사용하세요. 0과 1 사이의 값을 가질 수 있고 0.5로 설정 시, 정중앙에 위치하게 돼요.

**Example: AnchorPositionByRatio**

```tsx
<div style={{ display: "flex", gap: 10, paddingBottom: 80 }}>
  <Tooltip
    message={"툴팁입니다."}
    anchorPositionByRatio={0.1}
    openOnHover
    defaultOpen
  >
    <Button>0.1</Button>
  </Tooltip>
  <Tooltip
    message={"툴팁입니다."}
    anchorPositionByRatio={0.5}
    openOnHover
    defaultOpen
  >
    <Button>0.5</Button>
  </Tooltip>
  <Tooltip
    message={"툴팁입니다."}
    anchorPositionByRatio={0.9}
    openOnHover
    defaultOpen
  >
    <Button>0.9</Button>
  </Tooltip>
</div>
```

### 모션 강도 정하기

`Tooltip` 컴포넌트의 등장 퇴장 시, 발생하는 애니메이션의 강도를 정하려면 `motionVariant` 속성을 사용하세요.

**Example: MotionVariant**

```tsx
<div style={{ display: "flex", gap: 10, paddingBottom: 80 }}>
  <Tooltip message={"툴팁입니다."} motionVariant="weak" openOnHover>
    <Button>Weak</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} motionVariant="strong" openOnHover>
    <Button>Strong</Button>
  </Tooltip>
</div>
```

### position 속성 정하기

`Tooltip` 컴포넌트의 CSS `position` 속성을 정하려면 `strategy` 속성을 사용하세요.
다음 두 가지 속성이 사용가능해요.

- `absolute`: `Tooltip` 컴포넌트가 가장 가까운 `position`이 지정된 상위 요소를 기준으로 배치돼요. 대부분의 레이아웃에서는 브라우저가 위치를 업데이트할 때 보통 가장 적은 작업량을 요구해요.
- `fixed`: `Tooltip` 컴포넌트가 가장 가까운 포함 블록(보통 뷰포트)을 기준으로 배치돼요. `Tooltip` 컴포넌트가 고정되어 있을 때 스크롤 중 위치가 튀는 것을 줄이는 데 유용해요.

**Example: Strategy**

```tsx
<div style={{ display: "flex", gap: 10, paddingBottom: 80 }}>
  <Tooltip message={"툴팁입니다."} strategy="absolute" defaultOpen>
    <Button>absolute</Button>
  </Tooltip>
  <Tooltip message={"툴팁입니다."} strategy="fixed" defaultOpen>
    <Button>fixed</Button>
  </Tooltip>
</div>
```

## 인터페이스

**Type: TooltipProps**

```typescript
export interface TooltipProps {
  /**
   * `Tooltip` 컴포넌트의 크기에요.
   *
   * @default 'medium'
   */
  size?: "small" | "medium" | "large";
  /**
   * `Tooltip` 컴포넌트의 열림과 닫힘 상태를 내부에서 관리할 때 사용해요.
   *
   * @default false
   */
  defaultOpen?: boolean;
  /**
   * `Tooltip` 컴포넌트의 열림과 닫힘 상태를 외부에서 관리할 때 사용해요.
   *
   */
  open?: boolean;
  /**
   * `open` 상태가 변경될 때 호출되는 콜백 함수에요.
   */
  onOpenChange?: (open: boolean) => void;
  /**
   * `Tooltip` 컴포넌트에 표현할 메시지에요.
   */
  message?: ReactNode;
  /**
   * `Tooltip` 컴포넌트의 메세지의 정렬을 결정해요.
   *
   * @default 'left'
   */
  messageAlign?: "left" | "center" | "right";
  /**
   * `Tooltip` 컴포넌트를 `Tooltip` 컴포넌트의 트리거로부터 어떤 위치에 표현할지 결정해요.
   *
   * @default 'bottom'
   */
  placement?: "top" | "bottom";
  /**
   * `Tooltip` 컴포넌트의 등장과 퇴장 시 발생하는 모션의 강도에요.
   *
   * @default 'weak'
   */
  motionVariant?: "weak" | "strong";
  /**
   * `Tooltip` 컴포넌트와 `Tooltip` 컴포넌트 트리거까지의 거리를 표현해요.
   */
  offset?: number;
  /**
   * `Tooltip` 컴포넌트의 화살표 위치를 설정해요.
   * 0과 1 사이의 값을 갖고 기본값 설정 시 화살표가 메시지의 정중앙에 위치하게 돼요.
   *
   * @default 0.5
   */
  anchorPositionByRatio?: number;
  /**
   * 마우스 호버 시 `Tooltip` 컴포넌트가 열려요. 마우스 호버 상태가 풀리면 `Tooltip` 컴포넌트가 닫혀요.
   *
   * @default false
   */
  openOnHover?: boolean;
  /**
   * 포커스 시 `Tooltip` 컴포넌트가 열려요. 포커스가 상태가 풀리면 `Tooltip` 컴포넌트가 닫혀요.
   *
   * @default false
   */
  openOnFocus?: boolean;
  /**
   * `Tooltip` 컴포넌트 외부 클릭 시, `Tooltip` 컴포넌트가 닫혀요.
   *
   * @default false
   */
  dismissible?: boolean;
  /**
   * `Tooltip` 컴포넌트가 시야에서 벗어나는 경우, `Tooltip` 컴포넌트가 가려진 반대 방향으로 위치가 조정돼요.
   *
   * @default false
   */
  autoFlip?: boolean;
  /**
   * `Tooltip` 컴포넌트가 사용할 css `position`이에요.
   * 대부분의 경우 기본값인 `absolute`가 연산이 적어 적절해요.
   * @default 'absolute'
   */
  strategy?: "absolute" | "fixed";
  /**
   * `Tooltip` 컴포넌트의 화살표를 자르는 방향을 결정해요.
   * @default 'none'
   */
  clipToEnd?: "left" | "none" | "right";
}
```

---

# Top (/tds-mobile/components/top/)

# Top

[Image: Top thumbnail - top/Thumbnail-Top.png]

`Top` 컴포넌트는 다양한 레이아웃을 지원하는 페이지 상단 컴포넌트로, 여러 요소(텍스트, 버튼, 이미지 등)를 쉽게 배치할 수 있어요. 주로 페이지의 최상단에 사용되어 헤더나 타이틀 영역을 구성하는 데 활용돼요.

[Preview: Basic]

## 사용법

### 상하 여백 제어하기

`upperGap`와 `lowerGap` 속성을 사용해서 `Top` 컴포넌트의 상하 여백을 조정할 수 있어요.

**Example: TopBottomGap**

```tsx
<Top
  upperGap={0}
  lowerGap={0}
  title={<Top.TitleParagraph size={28}>동해물과 백두산이</Top.TitleParagraph>}
  right={<Top.RightButton>선택하기</Top.RightButton>}
/>
```

### 상단에 요소 추가하기

`upper` 속성을 사용해서 콘텐츠 영역 상단에 요소를 추가할 수 있어요. `Top` 컴포넌트의 여백 규칙을 지키려면 `Asset` 컴포넌트를 `Top.UpperAssetContent` 컴포넌트로 감싸서 사용해 주세요.

**Example: UpperAssetContent**

```tsx

      }
    />
  }
  title={<Top.TitleParagraph size={28}>동해물과 백두산이</Top.TitleParagraph>}
/>
```

### 하단에 요소 추가하기

`lower` 속성을 사용해서 콘텐츠 영역 하단에 요소를 추가할 수 있어요.

#### 하단에 버튼 한 개 추가하기

`Top.LowerButton` 컴포넌트를 사용해서 하단에 작은 버튼을 추가할 수 있어요.

**Example: LowerButton**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  lower={<Top.LowerButton>왜 사용할 수 없나요?</Top.LowerButton>}
/>
```

#### 하단에 버튼 두 개 추가하기

`Top.LowerCTA`와 `Top.LowerCTAButton` 컴포넌트를 사용해서 하단에 꽉 찬 두 개의 버튼을 표현할 수 있어요. `Top.LowerCTAButton`의 `display` 속성에 `block`을 설정하면 돼요.

**Example: LowerCTAButton**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  lower={
    <Top.LowerCTA
      type="2-button"
      leftButton={
        <Top.LowerCTAButton color="dark" variant="weak" display="block">
          채우기
        </Top.LowerCTAButton>
      }
      rightButton={
        <Top.LowerCTAButton display="block">보내기</Top.LowerCTAButton>
      }
    />
  }
/>
```

### 우측에 요소 추가하기

`right` 속성을 사용해서 콘텐츠 영역 우측에 요소를 추가할 수 있어요.

#### 우측에 에셋 추가하기

`Asset` 컴포넌트를 사용해서 우측에 원하는 에셋을 추가할 수 있어요. `Top` 컴포넌트의 여백 규칙을 지키려면 `Asset` 컴포넌트를 `Top.RightAssetContent` 컴포넌트로 감싸서 사용하면 돼요.

**Example: RightAssetContent**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  right={

      }
    />
  }
/>
```

#### 우측에 버튼 추가하기

`Top.RightButton` 컴포넌트를 사용해서 우측에 버튼을 추가할 수 있어요.

**Example: RightButton**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  right={
    <Top.RightButton color="dark" variant="weak">
      송금
    </Top.RightButton>
  }
/>
```

### 콘텐츠 영역에 타이틀 추가하기

`title` 속성을 사용해 콘텐츠 영역에 타이틀을 추가할 수 있어요.

타이틀 영역에 단순한 정보를 보여주려면 `Top.TitleParagraph` 컴포넌트를 사용할 수 있어요. 이 컴포넌트는 상호작용이 없는 단순한 정보 전달용이에요.

**Example: TitleParagraph**

```tsx
<Top title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>} />
```

#### 타이틀을 텍스트 버튼으로 추가하기

타이틀 영역에 링크와 같은 텍스트 버튼을 추가하려면 `Top.TitleTextButton` 컴포넌트를 사용할 수 있어요.
`Top.TitleTextButton`는 타이틀 영역이 텍스트 버튼처럼 동작하며, 클릭할 때 기본적인 인터렉션이 나타나요.

**Example: TitleTextButton**

```tsx
<Top title={<Top.TitleTextButton>동해물과 백두산이</Top.TitleTextButton>} />
```

#### 타이틀을 셀렉터 버튼으로 추가하기

타이틀 영역에 셀렉터 버튼을 추가할 때 `Top.TitleSelector` 컴포넌트를 사용할 수 있어요.
`Top.TitleSelector`는 타이틀 영역이 화살표 아이콘을 갖는 텍스트 버튼처럼 동작하고, 클릭할 때 기본적인 인터렉션이 나타나요.

**Example: TitleSelector**

```tsx
<Top title={<Top.TitleSelector>동해물과 백두산이</Top.TitleSelector>} />
```

### 콘텐츠 영역에 서브타이틀 추가하기

`subtitleTop`과 `subtitleBottom` 속성을 사용해 타이틀 상단 또는 하단에 서브타이틀을 추가할 수 있어요.

서브타이틀 영역에 단순한 정보를 보여줄 때는 `Top.SubtitleParagraph` 컴포넌트를 사용할 수 있어요. 이 컴포넌트는 상호작용 없이 정보만 전달해요.

**Example: SubtitleParagraph**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  subtitleTop={
    <Top.SubtitleParagraph>텍스트를 적어주세요.</Top.SubtitleParagraph>
  }
/>
```

#### 서브타이틀을 텍스트 버튼으로 추가하기

서브타이틀 영역에 링크와 같은 텍스트 버튼을 추가하려면 `Top.SubtitleTextButton` 컴포넌트를 사용할 수 있어요.
`Top.SubtitleTextButton`는 서브타이틀 영역이 텍스트 버튼처럼 동작하며, 클릭할 때 기본적인 인터렉션이 나타나요.

**Example: SubtitleTextButton**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  subtitleTop={
    <Top.SubtitleTextButton>텍스트를 적어주세요.</Top.SubtitleTextButton>
  }
/>
```

#### 서브타이틀을 셀렉터 버튼으로 추가하기

서브타이틀 영역에 셀렉터 버튼을 추가하려면 `Top.SubtitleSelector` 컴포넌트를 사용할 수 있어요. 이 컴포넌트는 화살표 아이콘이 포함된 버튼으로, 클릭할 때 인터렉션이 나타나요.

**Example: SubtitleSelector**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  subtitleTop={
    <Top.SubtitleSelector type="arrow">
      텍스트를 적어주세요.
    </Top.SubtitleSelector>
  }
/>
```

#### 서브타이틀을 뱃지로 추가하기

서브타이틀 영역에는 `Top.SubtitleBadges` 컴포넌트를 사용할 수 있어요. `badges` 속성에 원하는 뱃지 정보를 넣으면 돼요.

**Example: SubtitleBadges**

```tsx
<Top
  title={<Top.TitleParagraph>동해물과 백두산이</Top.TitleParagraph>}
  subtitleTop={}
/>
```

## 접근성

`Top` 컴포넌트는 기본적으로 접근성을 지원하는 여러 속성을 포함하고 있어요. 이 속성들은 스크린 리더 사용자들이 컴포넌트를 명확하게 이해하고 상호작용할 수 있도록 도와줘요.

| 속성                      | 접근성 효과                                                        | 설명                                                                                         |
| ------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- |
| `role="heading"`          | 스크린 리더에서 이 텍스트가 제목임을 인식해요.                     | 사용자는 콘텐츠의 계층을 쉽게 파악할 수 있어요.                                              |
| `aria-level="1"`          | 제목의 중요도를 스크린 리더에 전달해요.                            | 주요 제목임을 나타내고, 사용자는 이를 토대로 페이지 구조를 이해해요.                         |
| `aria-level="2"`          | 부제목의 계층을 스크린 리더로 전달해요.                            | 주요 제목 아래에 속하는 부제목임을 사용자에게 알려줘요.                                      |
| `aria-haspopup="listbox"` | 드롭다운을 사용하는 부분에서 스크린 리더가 팝업 메뉴임을 인식해요. | 사용자는 버튼을 누르면 기존 값을 다른 값으로 변경하는 팝업이 열린다는 것을 예측할 수 있어요. |

### 적용 예시

1. **Top.TitleParagraph**
   - `role="heading"` 속성과 `aria-level="1"` 속성을 적용하여 해당 텍스트가 주요 제목임을 명확하게 전달해요.
   ```jsx
   <Top.TitleParagraph role="heading" aria-level="1">
     주요 제목
   </Top.TitleParagraph>
   ```
2. **Top.SubtitleParagraph**
   - `role="heading"`과 `aria-level="2"` 속성을 추가하여 부제목임을 알리고, 텍스트 계층 구조를 명확히 해줘요.
   ```jsx
   <Top.SubtitleParagraph role="heading" aria-level="2">
     부제목
   </Top.SubtitleParagraph>
   ```
3. **Top.TitleSelector 및 Top.SubtitleSelector**
   - `aria-haspopup="listbox"` 속성이 자동으로 추가되어, 사용자는 버튼을 누르면 기존 값을 다른 값으로 변경하는 팝업이 열린다는 것을 예측할 수 있어요.
   ```jsx
   <Top.TitleSelector aria-haspopup="listbox">
     제목 선택
   </Top.TitleSelector>
   <Top.SubtitleSelector aria-haspopup="listbox">
     부제목 선택
   </Top.SubtitleSelector>
   ```

### 추가로 지원해야 하는 접근성

Top 컴포넌트는 기본적인 접근성을 제공하지만, 추가적인 속성을 활용해서 사용자 경험을 더욱 개선할 수 있어요. 예를 들어, aria-label을 사용해 제목이나 선택 항목의 의미가 명확하지 않을 때 적절한 설명을 추가하면 사용자가 더 쉽게 이해할 수 있어요.

## 인터페이스

**Type: TopProps**

```typescript
export interface TopProps {
  /**
   * 상단 여백을 지정해요.
   * @default 24
   */
  upperGap?: number;
  /**
   * 하단 여백을 지정해요.
   * @default 24
   */
  lowerGap?: number;
  /**
   * 콘텐츠 영역 상단에 표시될 부가적인 내용이에요.
   * 주로 `Asset`과 `Top.UpperAssetContent` 컴포넌트를 사용해요.
   */
  upper?: ReactNode;
  /**
   * 콘텐츠 영역 하단에 표시될 부가적인 내용이에요.
   * 주로 `Top.LowerButton`, `Top.LowerCTA`, 그리고 `Top.LowerCTAButton` 컴포넌트를 사용해요.
   */
  lower?: ReactNode;
  /**
   * 콘텐츠 영역에 표시될 타이틀이에요.
   * 주로 `Top.TitleParagraph`, `Top.TitleTextButton`, 그리고 `Top.TitleSelector` 컴포넌트를 사용해요.
   */
  title: ReactNode;
  /**
   * 타이틀 상단에 표시될 부가적인 내용이에요.
   * 주로 `Top.SubtitleParagraph`, `Top.SubtitleSelector`, `Top.SubtitleTextButton`, 그리고 `Top.SubtitleBadges` 컴포넌트를 사용해요.
   */
  subtitleTop?: ReactNode;
  /**
   * 타이틀 하단에 표시될 부가적인 내용이에요.
   * 주로 `Top.SubtitleParagraph`, `Top.SubtitleSelector`, `Top.SubtitleTextButton`, 그리고 `Top.SubtitleBadges` 컴포넌트를 사용해요.
   */
  subtitleBottom?: ReactNode;
  /**
   * 콘텐츠 영역 우측에 표시될 부가적인 내용이에요.
   * 주로 `Asset`, `Top.RightAssetContent`, 그리고  `Top.RightButton` 컴포넌트를 사용해요.
   */
  right?: ReactNode;
  /**
   * 콘텐츠 영역 우측의 수직 정렬을 제어해요.
   * @default 'center'
   */
  rightVerticalAlign?: "center" | "end";
}
```

**Type: TopLowerButtonProps**

```typescript
export interface TopLowerButtonProps extends ButtonProps {
  /**
   * 버튼의 크기를 지정해요.
   * @default 'small'
   */
  size?: "small" | "medium" | "large" | "xlarge";
}
```

**Type: TopLowerCTAProps**

```typescript
export interface TopLowerCTAProps {
  /**
   * 두 개의 버튼을 추가할 수 있어요.
   */
  type: "2-button";
  /**
   * 왼쪽 영역에 표시할 버튼이에요.
   */
  leftButton: React.ReactNode;
  /**
   * 오른쪽 영역에 표시할 버튼이에요.
   */
  rightButton: React.ReactNode;
}
```

**Type: TopLowerCTAButtonProps**

```typescript
export interface TopLowerCTAButtonProps extends ButtonProps {
  /**
   * 버튼의 크기를 지정해요.
   * @default 'large'
   */
  size?: "small" | "medium" | "large" | "xlarge";
}
```

**Type: TopRightArrowProps**

```typescript
export interface TopRightArrowProps extends IconProps {
  /**
   * 아이콘의 색상을 지정해요.
   * @default adaptive.grey600
   */
  color?: string;
  /**
   * 아이콘의 이름을 지정해요.
   * @default 'icon-arrow-right-small-mono'
   */
  name?: string;
}
```

**Type: TopRightAssetContentProps**

```typescript
export interface TopRightAssetContentProps {
  /**
   * 우측에 표시할 콘텐츠로, 주로 `Asset` 컴포넌트를 사용해요.
   */
  content: ReactNode;
}
```

**Type: TopRightButtonProps**

```typescript
export interface TopRightButtonProps extends ButtonProps {
  /**
   * 버튼의 크기를 지정해요.
   * @default 'medium'
   */
  size?: "small" | "medium" | "large" | "xlarge";
}
```

**Type: TopSubtitleBadgesProps**

```typescript
export interface TopSubtitleBadgesProps {
  /**
   * 표시할 뱃지의 배열이에요.
   */
  badges: Array<{
    /**
     * 뱃지에 표시할 텍스트에요.
     */
    text: string;
    /**
     * 뱃지의 색상을 설정해요.
     */
    type: "blue" | "teal" | "green" | "red" | "yellow" | "elephant";
    /**
     * 뱃지 스타일을 설정해요.
     * - `fill`: 채워진 스타일
     * - `weak`: 약한 스타일
     */
    style: "fill" | "weak";
  }>;
}
```

**Type: TopSubtitleParagraphProps**

```typescript
export interface TopSubtitleParagraphProps extends ParagraphProps {
  /**
   * 텍스트의 크기를 지정해요.
   * @default 17
   */
  size?: 13 | 15 | 17;
  /**
   * 텍스트의 색상을 지정해요.
   * @default adaptive.grey700
   */
  color?: string;
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * 텍스트 크기(`size`)에 따라 기본값이 다르게 적용돼요:
   * - size 13: t7
   * - size 15: t6
   * - size 17: t5
   * @default 't5'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트의 폰트 굵기를 지정해요.
   * 텍스트 크기(`size`)에 따라 기본값이 다르게 적용돼요:
   * - size 13: regular
   * - size 15: regular
   * - size 17: medium
   * @default 'medium'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: TopSubtitleSelectorProps**

```typescript
export interface TopSubtitleSelectorProps {
  /**
   * 셀렉터 버튼의 크기를 지정해요.
   * @default 17
   */
  size?: 13 | 15 | 17;
  /**
   * 셀렉터 버튼의 색상을 지정해요.
   * @default adaptive.grey700
   */
  color?: string;
  /**
   * 셀렉터 버튼의 타이포그래피 스타일을 지정해요.
   * `size`에 따라 기본값이 다르게 적용돼요:
   * - size 13: t7
   * - size 15: t6
   * - size 17: t5
   * @default 't5'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 셀렉터 버튼의 폰트 굵기를 지정해요.
   * `size`에 따라 기본값이 다르게 적용돼요:
   * - size 13: regular
   * - size 15: regular
   * - size 17: medium
   * @default 'medium'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: TopSubtitleTextButtonProps**

```typescript
export interface TopSubtitleTextButtonProps extends TextButtonProps {
  /**
   * 텍스트 버튼의 사이즈를 결정해요.
   * @default 'medium'
   */
  size?: "xsmall" | "small" | "medium" | "large" | "xlarge" | "xxlarge";
  /**
   * 텍스트 버튼의 형태를 결정해요.
   * @default 'arrow'
   */
  variant?: "arrow" | "underline" | "clear";
  /**
   * 텍스트 버튼의 색상을 지정해요.
   * @default adaptive.grey700
   */
  color?: string;
}
```

**Type: TopTitleParagraphProps**

```typescript
export interface TopTitleParagraphProps extends ParagraphProps {
  /**
   * 텍스트의 크기를 지정해요.
   * @default 22
   */
  size?: 22 | 28;
  /**
   * 텍스트의 색상을 지정해요.
   * @default adaptive.grey800
   */
  color?: string;
  /**
   * 텍스트의 타이포그래피 스타일을 지정해요.
   * `size`에 따라 기본값이 다르게 적용돼요:
   * - size 22: t3
   * - size 28: st2
   * @default 't3'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 텍스트의 폰트 굵기를 지정해요.
   * @default 'bold'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: TopTitleSelectorProps**

```typescript
export interface TopTitleSelectorProps {
  /**
   * 셀렉터 버튼의 색상을 지정해요.
   * @default adaptive.grey800
   */
  color?: string;
  /**
   * 셀렉터 버튼의 타이포그래피 스타일을 지정해요.
   * `size`에 따라 기본값이 다르게 적용돼요:
   * - size 22: t3
   * - size 28: st2
   * @default 't3'
   */
  typography?:
    | "t1"
    | "st1"
    | "st2"
    | "st3"
    | "t2"
    | "st4"
    | "st5"
    | "st6"
    | "t3"
    | "st7"
    | "t4"
    | "st8"
    | "st9"
    | "t5"
    | "st10"
    | "t6"
    | "st11"
    | "t7"
    | "st12"
    | "st13";
  /**
   * 셀렉터 버튼의 폰트 굵기를 지정해요.
   * @default 'bold'
   */
  fontWeight?: "regular" | "medium" | "semibold" | "bold";
}
```

**Type: TopTitleTextButtonProps**

```typescript
export interface TopTitleTextButtonProps extends TextButtonProps {
  /**
   * 텍스트 버튼의 사이즈를 결정해요.
   * @default 'xlarge'
   */
  size?: "xsmall" | "small" | "medium" | "large" | "xlarge" | "xxlarge";
  /**
   * 텍스트 버튼의 색상을 지정해요.
   * @default adaptive.grey800
   */
  color?: string;

  /**
   * 텍스트 버튼의 형태를 경정해요.
   */
  variant?: "arrow" | "underline" | "clear";
}
```

**Type: TopUpperAssetContentProps**

```typescript
export interface TopUpperAssetContentProps {
  /**
   * 주로 `Asset` 컴포넌트를 사용해요.
   */
  content: ReactNode;
}
```

---

# Colors (/tds-mobile/foundation/colors/)

# Colors

토스의 색상 시스템은 개발자와 디자이너가 **통일된 색상 이름**을 사용하도록 도와줘요.
이 시스템을 활용하면 디자인 가이드에 맞춰 일관된 UI를 쉽게 구현할 수 있어요.

## 기본 사용법

토스의 색상 시스템을 사용하려면 `@toss/tds-colors` 패키지를 설치해야 해요.

```bash copy
yarn add @toss/tds-colors
```

설치가 끝나면 `colors` 객체에서 원하는 색상을 가져와 사용할 수 있어요.

```jsx
import { colors } from "@toss/tds-colors";

<div style={{ width: 100, height: 100, backgroundColor: colors.blue500 }} />;
```

## 기본 색상

[Preview: div]

## 배경 색상

[Preview: BackgroundPalette]

---

# Typography (/tds-mobile/foundation/typography/)

# Typography

Typography는 디자인 시스템의 핵심 요소로, 텍스트의 가독성을 보장하고 일관된 방향성을 유지하며 브랜드 아이덴티티를 전달하는 중요한 역할을 해요. 폰트 크기, 라인 높이 등을 통해 정보의 계층 구조를 명확히 하고, 다양한 디바이스와 환경에서 통일된 비주얼을 제공하는 데 초점을 맞춰요.

우리의 디자인 시스템은 다양한 플랫폼에서의 일관된 사용자 경험을 제공하기 위해 설계되었어요. 안드로이드와 iOS뿐 아니라, 웹 페이지에서도 이질감 없이 동일한 텍스트 스타일이 적용될 수 있도록 명확한 규칙을 따르고 있어요. 특히 네이티브 환경에서의 더 큰 텍스트 모드와 같은 접근성 옵션을 지원하며, 폰트 크기와 텍스트 스타일이 이에 맞춰 동적으로 조정되도록 설계했어요.

## 규칙 알아보기

### 토큰

Typography 토큰은 계층 구조를 가지고 있어요. 사용 방법은 아래 표에서 확인할 수 있어요. Typography를 **사용하는 입장에서 구체적인 폰트 크기와 라인 높이를 외우거나 직접 계산할 필요는 없어요.** 사용자는 계층화된 토큰을 그대로 사용하도록 추상화되어 있어요.

또한, **아래 표에 나온 값을 직접 하드코딩하지 않길 권장해요.** 이 표는 더 큰 텍스트가 적용되지 않은 기본적인 상황을 가정한 것이며, 값을 직접 하드코딩하면 더 큰 텍스트로 인해 시스템의 폰트 크기가 변경되는 상황에서 유연하게 대응하기 어려울 수 있어요.

[Preview: Token]

### 더 큰 텍스트

더 큰 텍스트는 iOS와 Android에서 제공하는 접근성 설정으로, 사용자가 텍스트 크기를 조정해 가독성을 높이는 기능이에요. 이 설정은 네이티브 환경뿐 아니라 앱 내부의 웹 페이지에서도 동일하게 적용되어야 해요. 네이티브 설정으로 텍스트 비율이 커진 경우, 웹 페이지 본문 텍스트가 상대적으로 작아 가독성이 떨어질 수 있기 때문이에요.

이런 문제를 방지하려면, 사용자가 기기에서 더 큰 텍스트 모드를 활성화하고 비율을 변경했을 때 적용되는 실제 폰트 크기를 아래 표에 정리했어요. 이 표를 참고하면 네이티브와 웹 간 텍스트 비율 차이를 줄이고 모든 환경에서 일관된 사용자 경험을 제공할 수 있어요. 표에 나온 값을 고정 값으로 하드코딩하지 않는 것이 중요해요. 하드코딩된 값은 더 큰 텍스트 모드에서 유연한 대응을 어렵게 만들 수 있어요.

Android, iOS, 웹 간의 차이로 인해 완벽히 동일한 규칙을 적용하기는 어려워요. 하지만 플랫폼 간 차이를 최소화하기 위해 근사한 값을 기준으로 규칙을 마련했어요. 아래에서 이를 확인할 수 있어요.

#### iOS

iOS는 xLarge와, xxLarge와, xxxLarge와와 같이 제한된 수의 더 큰 텍스트 단계를 제공해요. 우리는 이 단계를 비율로 추상화해서 Android, iOS, 그리고 웹 간의 규칙을 일관되게 맞췄어요. 아래 표에서는 네이티브 환경의 각 설정에 따라 웹에서 보여줘야 할 값을 확인할 수 있어요.

[Preview: Component]

#### Android

한편, Android는 iOS와 달리 100% 이상의 모든 값을 지원하고 제한된 단계로 표현할 수 없어요. 그래서 다음 표와 같은 규칙을 마련했어요. 표에 표시된 NN%는 비율을 나타내요.

예를 들어 사용자가 110%로 설정하고 Typography 1 토큰을 사용했다면, 해당 토큰의 공식(`30 x NN x 0.01`)에 따라 33으로 계산돼요.

[Preview: Component]

## 전체 보기

[Preview: Basic]

---

# Overlay Extension 이해하기 (/tds-mobile/hooks/OverlayExtension/check-first/)

# Overlay Extension 이해하기

이 문서를 읽고나면,

- `useDialog`, `useToast`, `useBottomSheet` 훅의 차이점과 각각의 사용 목적을 이해할 수 있어요. 각 훅이 제공하는 기능과 사용 방법을 이해할 수 있어요.

[Preview: Basic]

## 이해하기

`OverlayExtension`은 [`Dialog` 컴포넌트](/components/dialog/dialog), [`Toast` 컴포넌트](/components/toast), [`BottomSheet` 컴포넌트](/components/bottom-sheet)와 같은 오버레이 UI를 선언적으로 쉽게 사용할 수 있게 해주는 유틸리티 훅들의 모음이에요.

### useDialog vs useToast vs useBottomSheet

각 훅은 서로 다른 목적과 사용 상황에 맞게 설계되어 있어요:

| 훅               | 설명                                                            | 사용 상황                                                                        | 문서                                                            |
| :--------------- | :-------------------------------------------------------------- | :------------------------------------------------------------------------------- | :-------------------------------------------------------------- |
| `useDialog`      | 사용자의 주의가 필요한 중요한 정보나 결정을 요구할 때 사용해요. | - 중요한 작업 확인<br/>- 경고 메시지 표시<br/>- 사용자의 명시적 결정이 필요할 때 | [useDialog 문서](/hooks/OverlayExtension/use-dialog)            |
| `useToast`       | 일시적인 알림이나 피드백을 표시할 때 사용해요.                  | - 작업 완료 알림<br/>- 오류 메시지<br/>- 일시적인 상태 표시                      | [useToast 문서](/hooks/OverlayExtension/use-toast)              |
| `useBottomSheet` | 추가 정보나 작업을 화면 하단에서 표시할 때 사용해요.            | - 상세 정보 표시<br/>- 추가 옵션 제공<br/>- 복잡한 상호작용이 필요할 때          | [useBottomSheet 문서](/hooks/OverlayExtension/use-bottom-sheet) |

---

# useBottomSheet (/tds-mobile/hooks/OverlayExtension/use-bottom-sheet/)

# useBottomSheet

`useBottomSheet` 훅은 화면 하단에서 올라오는 바텀시트를 쉽게 제어할 수 있게 해주는 유틸리티 훅이에요. 이 훅을 사용하면 바텀시트의 열림과 닫힘 상태를 제어하고, 콘텐츠 표시와 사용자 상호작용을 효율적으로 처리할 수 있어요. 이를 통해 반복적인 코드를 줄이고, 바텀시트를 일관되게 구현할 수 있어요.

[Preview: Basic]

## 사용 예시

### 기본 바텀시트 표시하기

`open` 메서드를 사용하여 기본적인 바텀시트를 표시할 수 있어요.

- `header` 속성으로 제목을, `children`으로 내용을 전달할 수 있어요.
- `closeOnDimmerClick` 속성을 사용해 배경 클릭 시 바텀시트가 닫히는 동작을 제어할 수 있어요. 기본값은 `true`예요.

**Example: Basic**

```tsx
function Basic() {
  const { open, close } = useBottomSheet();

  return (
    <Button
      onClick={() => {
        open({
          header: "기본 바텀시트예요",
          children: (
            <Text style={{ margin: "0 24px 24px 24px" }}>
              컨텐츠만 있는 기본적인 바텀시트예요.
            </Text>
          ),
          onClose: () => close(),
        });
      }}
    >
      기본 바텀시트 열기
    </Button>
  );
}
```

### 단일 버튼 바텀시트

`openOneButtonSheet` 메서드를 사용하면 하나의 버튼이 있는 바텀시트를 표시할 수 있어요.

- `button` 속성으로 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요. 문자열을 전달하면 기본 버튼이 생성돼요.
- `closeOnButtonClick` 속성으로 버튼을 클릭했을 때 바텀시트가 닫히는 동작을 제어할 수 있어요.

**Example: OneButtonSheet**

```tsx
function OneButtonSheet() {
  const { openOneButtonSheet } = useBottomSheet();

  return (
    <Button
      onClick={() => {
        openOneButtonSheet({
          header: "단일 버튼 바텀시트예요",
          children: (
            <Text style={{ margin: "0 24px" }}>
              하나의 버튼이 있는 바텀시트예요.
            </Text>
          ),
          button: "확인",
        });
      }}
    >
      단일 버튼 바텀시트 열기
    </Button>
  );
}
```

### 이중 버튼 바텀시트

`openTwoButtonSheet` 메서드로 두 개의 버튼이 있는 바텀시트를 표시할 수 있어요.

- `leftButton`과 `rightButton` 속성으로 각 버튼을 설정하고, `closeOnLeftButtonClick`과 `closeOnRightButtonClick`으로 각 버튼을 클릭할 때의 닫힘 동작을 제어할 수 있어요.

**Example: TwoButtonSheet**

```tsx
function TwoButtonSheet() {
  const { openTwoButtonSheet } = useBottomSheet();

  return (
    <Button
      onClick={async () => {
        await openTwoButtonSheet({
          header: "이중 버튼 바텀시트예요",
          children: (
            <Text style={{ margin: "0 24px" }}>
              두 개의 버튼이 있는 바텀시트예요.
            </Text>
          ),
          leftButton: "취소",
          rightButton: "확인",
        });
      }}
    >
      이중 버튼 바텀시트 열기
    </Button>
  );
}
```

### 비동기 작업 처리하기

`openAsyncTwoButtonSheet` 메서드를 사용하면 버튼을 클릭할 때 버튼에 로딩 중임이 표현되고, 조건이 만족할 때까지 바텀시트를 표시할 수 있어요. 이 방법은 작업이 끝날 때까지 바텀시트를 유지해야 할 때 유용해요.

- `onLeftButtonClick`과 `onRightButtonClick` 속성에 비동기 함수를 전달하면, 작업이 완료될 때까지 자동으로 로딩 상태가 처리돼요.

**Example: AsyncSheet**

```tsx
function AsyncSheet() {
  const { openAsyncTwoButtonSheet } = useBottomSheet();

  const delay = async (milliseconds: number) => {
    await new Promise((res) => setTimeout(res, milliseconds));
  };

  return (
    <Button
      onClick={() => {
        openAsyncTwoButtonSheet({
          header: "결제를 취소할까요?",
          children: (
            <Text style={{ margin: "0 24px" }}>
              결제를 취소하면 되돌릴 수 없어요.
            </Text>
          ),
          leftButton: "취소",
          rightButton: "확인",
          onRightButtonClick: () => delay(1000),
        });
      }}
    >
      비동기 바텀시트 열기
    </Button>
  );
}
```

## 인터페이스

**Type: BottomSheetOptions**

```typescript
export interface BottomSheetOptions {
  /**
   * `BottomSheet` 컴포넌트의 헤더에 표시될 제목이에요.
   */
  header?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 내용이에요.
   */
  children: ReactNode;

  /**
   * `BottomSheet` 컴포넌트 외부의 어두운 배경을 클릭했을 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `BottomSheet` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;

  /**
   * `BottomSheet` 컴포넌트가 열렸을 때 `BottomSheet` 컴포넌트 외부 영역에서:
   * - 키보드 포커스가 `BottomSheet` 컴포넌트 내부로 제한되지 않도록 하고
   * - 스크린 리더가 `BottomSheet` 컴포넌트 외부 콘텐츠를 읽을 수 있도록 해요.
   *
   * 이 속성을 사용하면 접근성이 제한될 수 있으므로 불가피한 경우에만 사용해주세요.
   */
  UNSAFE_disableFocusLock?: boolean;

  /**
   * `BottomSheet` 컴포넌트 외부의 어두운 배경을 클릭해도 onClose가 호출되지 않게 해요.
   *
   * **주의: `BottomSheet` 컴포넌트 외부 영역 클릭 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   */
  UNSAFE_ignoreDimmerClick?: boolean;

  /**
   * 앱에서 제공하는 뒤로가기 이벤트를 무시할지 설정해요.
   * true로 설정하면 뒤로가기 동작이 발생해도 `BottomSheet` 컴포넌트가 닫히지 않아요.
   *
   * **주의: 뒤로가기 동작 발생 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   * 추후 이 api가 deprecated 될 수 있으므로, 취소 액션을 구현하는 것이 기술적으로 어려운 상황에서만 이 속성을 사용해 주세요.
   */
  UNSAFE_ignoreBackEvent?: boolean;
}
```

**Type: OneButtonOptions**

```typescript
export interface OneButtonOptions {
  /**
   * `BottomSheet` 컴포넌트의 헤더에 표시될 제목이에요.
   */
  header?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 내용이에요.
   */
  children: ReactNode;

  /**
   * 배경을 클릭했을 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `BottomSheet` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;

  /**
   * `BottomSheet` 컴포넌트 상단에 표시될 요소에요.
   */
  topAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트 하단에 표시될 요소에요.
   */
  bottomAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  button?: ReactElement | string;

  /**
   * 버튼을 클릭할 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnButtonClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열렸을 때 `BottomSheet` 컴포넌트 외부 영역에서:
   * - 키보드 포커스가 `BottomSheet` 컴포넌트 내부로 제한되지 않도록 하고
   * - 스크린 리더가 `BottomSheet` 컴포넌트 외부 콘텐츠를 읽을 수 있도록 해요.
   *
   * 이 속성을 사용하면 접근성이 제한될 수 있으므로 불가피한 경우에만 사용해주세요.
   */
  UNSAFE_disableFocusLock?: boolean;

  /**
   * `BottomSheet` 컴포넌트 외부의 어두운 배경을 클릭해도 onClose가 호출되지 않게 해요.
   *
   * **주의: `BottomSheet` 컴포넌트 외부 영역 클릭 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   */
  UNSAFE_ignoreDimmerClick?: boolean;

  /**
   * 앱에서 제공하는 뒤로가기 이벤트를 무시할지 설정해요.
   * true로 설정하면 뒤로가기 동작이 발생해도 `BottomSheet` 컴포넌트가 닫히지 않아요.
   *
   * **주의: 뒤로가기 동작 발생 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   * 추후 이 api가 deprecated 될 수 있으므로, 취소 액션을 구현하는 것이 기술적으로 어려운 상황에서만 이 속성을 사용해 주세요.
   */
  UNSAFE_ignoreBackEvent?: boolean;
}
```

**Type: AsyncOneButtonOptions**

```typescript
export interface AsyncOneButtonOptions {
  /**
   * `BottomSheet` 컴포넌트의 헤더에 표시될 제목이에요.
   */
  header?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 내용이에요.
   */
  children: ReactNode;

  /**
   * 배경을 클릭했을 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `BottomSheet` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;

  /**
   * `BottomSheet` 컴포넌트 상단에 표시될 요소에요.
   */
  topAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트 하단에 표시될 요소에요.
   */
  bottomAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  button?: ReactElement | string;

  /**
   * 버튼을 클릭할 때 실행될 비동기 함수에요.
   */
  onClick?: () => Promise<void>;

  /**
   * 버튼의 로딩 상태를 나타내는 prop의 이름이에요.
   *
   * @default 'loading'
   */
  loadingPropName?: string;

  /**
   * `BottomSheet` 컴포넌트가 열렸을 때 `BottomSheet` 컴포넌트 외부 영역에서:
   * - 키보드 포커스가 `BottomSheet` 컴포넌트 내부로 제한되지 않도록 하고
   * - 스크린 리더가 `BottomSheet` 컴포넌트 외부 콘텐츠를 읽을 수 있도록 해요.
   *
   * 이 속성을 사용하면 접근성이 제한될 수 있으므로 불가피한 경우에만 사용해주세요.
   */
  UNSAFE_disableFocusLock?: boolean;

  /**
   * `BottomSheet` 컴포넌트 외부의 어두운 배경을 클릭해도 onClose가 호출되지 않게 해요.
   *
   * **주의: `BottomSheet` 컴포넌트 외부 영역 클릭 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   */
  UNSAFE_ignoreDimmerClick?: boolean;

  /**
   * 앱에서 제공하는 뒤로가기 이벤트를 무시할지 설정해요.
   * true로 설정하면 뒤로가기 동작이 발생해도 `BottomSheet` 컴포넌트가 닫히지 않아요.
   *
   * **주의: 뒤로가기 동작 발생 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   * 추후 이 api가 deprecated 될 수 있으므로, 취소 액션을 구현하는 것이 기술적으로 어려운 상황에서만 이 속성을 사용해 주세요.
   */
  UNSAFE_ignoreBackEvent?: boolean;
}
```

**Type: TwoButtonOptions**

```typescript
export interface TwoButtonOptions {
  /**
   * `BottomSheet` 컴포넌트의 헤더에 표시될 제목이에요.
   */
  header?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 내용이에요.
   */
  children: ReactNode;

  /**
   * 배경을 클릭했을 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `BottomSheet` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;

  /**
   * `BottomSheet` 컴포넌트 상단에 표시될 요소에요.
   */
  topAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트 하단에 표시될 요소에요.
   */
  bottomAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 왼쪽 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '취소'
   */
  leftButton?: ReactElement | string;

  /**
   * 왼쪽 버튼을 클릭할 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnLeftButtonClick?: boolean;

  /**
   * 오른쪽 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  rightButton?: ReactElement | string;

  /**
   * 오른쪽 버튼을 클릭할 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnRightButtonClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열렸을 때 `BottomSheet` 컴포넌트 외부 영역에서:
   * - 키보드 포커스가 `BottomSheet` 컴포넌트 내부로 제한되지 않도록 하고
   * - 스크린 리더가 `BottomSheet` 컴포넌트 외부 콘텐츠를 읽을 수 있도록 해요.
   *
   * 이 속성을 사용하면 접근성이 제한될 수 있으므로 불가피한 경우에만 사용해주세요.
   */
  UNSAFE_disableFocusLock?: boolean;

  /**
   * `BottomSheet` 컴포넌트 외부의 어두운 배경을 클릭해도 onClose가 호출되지 않게 해요.
   *
   * **주의: `BottomSheet` 컴포넌트 외부 영역 클릭 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   */
  UNSAFE_ignoreDimmerClick?: boolean;

  /**
   * 앱에서 제공하는 뒤로가기 이벤트를 무시할지 설정해요.
   * true로 설정하면 뒤로가기 동작이 발생해도 `BottomSheet` 컴포넌트가 닫히지 않아요.
   *
   * **주의: 뒤로가기 동작 발생 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   * 추후 이 api가 deprecated 될 수 있으므로, 취소 액션을 구현하는 것이 기술적으로 어려운 상황에서만 이 속성을 사용해 주세요.
   */
  UNSAFE_ignoreBackEvent?: boolean;
}
```

**Type: AsyncTwoButtonOptions**

```typescript
export interface AsyncTwoButtonOptions {
  /**
   * `BottomSheet` 컴포넌트의 헤더에 표시될 제목이에요.
   */
  header?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 내용이에요.
   */
  children: ReactNode;

  /**
   * 배경을 클릭했을 때 `BottomSheet` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default true
   */
  closeOnDimmerClick?: boolean;

  /**
   * `BottomSheet` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `BottomSheet` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;

  /**
   * `BottomSheet` 컴포넌트 상단에 표시될 요소에요.
   */
  topAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트 하단에 표시될 요소에요.
   */
  bottomAccessory?: ReactNode;

  /**
   * `BottomSheet` 컴포넌트의 왼쪽 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '취소'
   */
  leftButton?: ReactElement | string;

  /**
   * 왼쪽 버튼을 클릭할 때 실행될 비동기 함수에요.
   */
  onLeftButtonClick?: () => Promise<void>;

  /**
   * 왼쪽 버튼의 로딩 상태를 나타내는 prop의 이름이에요.
   *
   * @default 'loading'
   */
  leftButtonLoadingPropName?: string;

  /**
   * `BottomSheet` 컴포넌트의 오른쪽 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  rightButton?: ReactElement | string;

  /**
   * 오른쪽 버튼을 클릭할 때 실행될 비동기 함수에요.
   */
  onRightButtonClick?: () => Promise<void>;

  /**
   * 오른쪽 버튼의 로딩 상태를 나타내는 prop의 이름이에요.
   *
   * @default 'loading'
   */
  rightButtonLoadingPropName?: string;

  /**
   * `BottomSheet` 컴포넌트가 열렸을 때 `BottomSheet` 컴포넌트 외부 영역에서:
   * - 키보드 포커스가 `BottomSheet` 컴포넌트 내부로 제한되지 않도록 하고
   * - 스크린 리더가 `BottomSheet` 컴포넌트 외부 콘텐츠를 읽을 수 있도록 해요.
   *
   * 이 속성을 사용하면 접근성이 제한될 수 있으므로 불가피한 경우에만 사용해주세요.
   */
  UNSAFE_disableFocusLock?: boolean;

  /**
   * `BottomSheet` 컴포넌트 외부의 어두운 배경을 클릭해도 onClose가 호출되지 않게 해요.
   *
   * **주의: `BottomSheet` 컴포넌트 외부 영역 클릭 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   */
  UNSAFE_ignoreDimmerClick?: boolean;

  /**
   * 앱에서 제공하는 뒤로가기 이벤트를 무시할지 설정해요.
   * true로 설정하면 뒤로가기 동작이 발생해도 `BottomSheet` 컴포넌트가 닫히지 않아요.
   *
   * **주의: 뒤로가기 동작 발생 시 사용자의 액션을 취소하고 `BottomSheet` 컴포넌트가 닫히는 것이 권장되는 동작이에요.**
   * 추후 이 api가 deprecated 될 수 있으므로, 취소 액션을 구현하는 것이 기술적으로 어려운 상황에서만 이 속성을 사용해 주세요.
   */
  UNSAFE_ignoreBackEvent?: boolean;
}
```

---

# useDialog (/tds-mobile/hooks/OverlayExtension/use-dialog/)

# useDialog

`useDialog` 훅은 Alert와 Confirm 형태의 다이얼로그를 쉽게 표시할 수 있게 해주는 유틸리티 훅이에요.

[Preview: Basic]

## 사용 예시

### Alert 다이얼로그 표시하기

`openAlert` 메서드를 사용하여 기본적인 Alert 다이얼로그를 표시할 수 있어요.
`title`로 제목을, `description`으로 설명을 설정할 수 있고, `alertButton` 속성으로 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
`closeOnDimmerClick` 속성을 `false`로 설정하면 배경 클릭으로 다이얼로그가 닫히는 것을 방지할 수 있어요.

**Example: Basic**

```tsx
function Basic() {
  const { openAlert } = useDialog();

  return (
    <Button
      onClick={() => {
        openAlert({
          title: "알려드릴게요",
          description: "작업이 완료됐어요.",
          alertButton: "확인하기",
        });
      }}
    >
      기본 Alert 다이얼로그 열기
    </Button>
  );
}
```

### Confirm 다이얼로그 표시하기

`openConfirm` 메서드는 사용자의 결정을 요구하는 상황에서 유용해요.
`confirmButton`과 `cancelButton` 속성으로 각 버튼의 텍스트를 지정하거나, 커스텀 버튼을 사용할 수 있어요.

**Example: BasicConfirm**

```tsx
function BasicConfirm() {
  const { openConfirm } = useDialog();

  return (
    <Button
      onClick={() => {
        openConfirm({
          title: "삭제할까요?",
          description: "이 작업은 되돌릴 수 없어요.",
          confirmButton: "삭제하기",
          cancelButton: "취소",
        });
      }}
    >
      기본 Confirm 다이얼로그 열기
    </Button>
  );
}
```

### 비동기 작업 처리하기

`openAsyncConfirm`을 사용하면 버튼을 클릭했을 때 로딩 상태를 표시하면서 비동기 작업을 처리할 수 있어요.
`onConfirmClick`과 `onCancelClick` 속성에 비동기 함수를 전달하면, 작업이 완료될 때까지 자동으로 로딩 상태가 처리돼요.

**Example: AsyncConfirm**

```tsx
function AsyncConfirm() {
  const { openAsyncConfirm } = useDialog();

  const delay = async (milliseconds: number) => {
    await new Promise((res) => setTimeout(res, milliseconds));
  };

  return (
    <Button
      onClick={() => {
        openAsyncConfirm({
          title: "상담을 종료할까요?",
          description: "상담을 종료하면 대화를 이어갈 수 없어요.",
          confirmButton: "종료하기",
          cancelButton: "취소",
          onConfirmClick: () => delay(2000),
        });
      }}
    >
      비동기 Confirm 다이얼로그 열기
    </Button>
  );
}
```

## 인터페이스

**Type: AlertOptions**

```typescript
export interface AlertOptions {
  /**
   * `AlertDialog` 컴포넌트의 제목이에요.
   */
  title: ReactNode;

  /**
   * `AlertDialog` 컴포넌트의 설명이에요.
   */
  description?: ReactNode;

  /**
   * `AlertDialog` 컴포넌트의 확인 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  alertButton?: "ReactElement | string";

  /**
   * 배경을 클릭했을 때 `AlertDialog` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default false
   */
  closeOnDimmerClick?: boolean;

  /**
   * `AlertDialog` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `AlertDialog` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;
}
```

**Type: ConfirmOptions**

```typescript
export interface ConfirmOptions {
  /**
   * `ConfirmDialog` 컴포넌트의 제목이에요.
   */
  title: ReactNode;

  /**
   * `ConfirmDialog` 컴포넌트의 설명이에요.
   */
  description?: ReactNode;

  /**
   * 배경을 클릭했을 때 `ConfirmDialog` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default false
   */
  closeOnDimmerClick?: boolean;

  /**
   * `ConfirmDialog` 컴포넌트의 확인 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  confirmButton?: "ReactElement | string";

  /**
   * `ConfirmDialog` 컴포넌트의 취소 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '취소'
   */
  cancelButton?: "ReactElement | string";

  /**
   * `ConfirmDialog` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `ConfirmDialog` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;
}
```

**Type: AsyncConfirmOptions**

```typescript
export interface AsyncConfirmOptions {
  /**
   * `AsyncConfirmDialog` 컴포넌트의 제목이에요.
   */
  title: ReactNode;

  /**
   * `AsyncConfirmDialog` 컴포넌트의 설명이에요.
   */
  description?: ReactNode;

  /**
   * 배경을 클릭했을 때 `AsyncConfirmDialog` 컴포넌트가 닫힐지 여부를 설정해요.
   *
   * @default false
   */
  closeOnDimmerClick?: boolean;

  /**
   * `AsyncConfirmDialog` 컴포넌트가 열린 후 실행될 콜백 함수에요.
   */
  onEntered?: () => void;

  /**
   * `AsyncConfirmDialog` 컴포넌트가 닫힌 후 실행될 콜백 함수에요.
   */
  onExited?: () => void;

  /**
   * `AsyncConfirmDialog` 컴포넌트의 확인 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '확인'
   */
  confirmButton?: "ReactElement | string";

  /**
   * 확인 버튼을 클릭할 때 실행될 비동기 함수에요.
   */
  onConfirmClick?: () => Promise<void>;

  /**
   * 확인 버튼의 로딩 상태를 나타내는 prop의 이름이에요.
   *
   * @default 'loading'
   */
  confirmButtonLoadingPropName?: string;

  /**
   * `AsyncConfirmDialog` 컴포넌트의 취소 버튼이에요.
   *
   * 버튼의 텍스트나 커스텀 버튼을 설정할 수 있어요.
   *
   * @default '취소'
   */
  cancelButton?: "ReactElement | string";

  /**
   * 취소 버튼을 클릭할 때 실행될 비동기 함수에요.
   */
  onCancelClick?: () => Promise<void>;

  /**
   * 취소 버튼의 로딩 상태를 나타내는 prop의 이름이에요.
   *
   * @default 'loading'
   */
  cancelButtonLoadingPropName?: string;
}
```

---

# useToast (/tds-mobile/hooks/OverlayExtension/use-toast/)

# useToast

`useToast`는 간단하고 일시적인 알림 메시지를 화면에 표시할 수 있게 해주는 유틸리티 훅이에요. 사용자에게 피드백을 제공하거나 이벤트를 알릴 때 유용하게 사용할 수 있어요.

[Preview: Basic]

## 동작 방식

#### 웹 환경

- 기본적으로 토스트 메시지는 자동으로 사라져요.
  - 버튼이 없을 때: 3000ms 후에 사라져요.
  - 버튼이 있을 때: 5000ms 후에 사라져요.
- `duration` 속성을 사용해 표시 시간을 원하는 대로 설정할 수 있어요.
- `closeToast` 메서드를 통해 수동으로 닫을 수도 있어요.

#### 앱 환경

- Android와 iOS에서 기본 위치가 다르게 설정돼요.
  - Android: 화면 기준 상단 26px 떨어진 곳에 위치해요.
  - iOS: 화면 기준 상단 46px 떨어진 곳에 위치해요.
- `SafeArea`와 `BottomCTA` 컴포넌트의 높이를 자동으로 고려해요.
- 수동으로 닫는 메서드는 제공되지 않고, 앱브릿지가 있는 환경에서 사용돼요.

## 사용 예시

### 기본 토스트 메시지 표시하기

가장 단순한 토스트 메시지를 표시하는 예시예요. `message` 속성을 통해 표시할 내용을 설정하고, `openToast` 메서드를 호출해요.

**Example: Basic**

```tsx
function Basic() {
  const toast = useToast();

  return (
    <Button
      onClick={() => {
        toast.openToast("메시지를 전송했어요");
      }}
    >
      기본 토스트 열기
    </Button>
  );
}
```

### 아이콘과 함께 사용하기

`icon` 속성을 사용하여 토스트 메시지에 원하는 아이콘을 자유롭게 사용할 수 있으며, 이를 통해 더 명확한 시각적 피드백을 제공할 수 있어요.

**Example: IconToast**

```tsx
function IconToast() {
  const toast = useToast();

  return (
    <Button
      onClick={() => {
        toast.openToast("프로필을 업데이트했어요", {
          icon: "icon-check",
          iconType: "circle",
        });
      }}
    >
      아이콘 토스트 열기
    </Button>
  );
}
```

### 버튼과 함께 사용하기

`button` 속성을 사용해서 토스트 메시지에 버튼을 추가할 수 있어요. 버튼이 있을 때 웹 환경에서는 기본적으로 5초 동안 표시되고, `onClick` 속성으로 버튼을 클릭할 때의 동작을 정의할 수 있어요.

**Example: ButtonToast**

```tsx
function ButtonToast() {
  const toast = useToast();

  return (
    <Button
      onClick={() => {
        toast.openToast("결제에 실패했어요", {
          icon: "icon-warning-circle",
          button: {
            text: "다시 시도하기",
            onClick: () => alert("결제 재시도"),
          },
        });
      }}
    >
      버튼 토스트 열기
    </Button>
  );
}
```

### 위치 조정하기

`type` 속성을 사용하여 토스트 메시지의 위치를 'top' 또는 'bottom'으로 설정할 수 있어요.
앱 환경에서는 OS별로 최적화된 기본 위치값이 적용되며, `SafeArea`와 `BottomCTA`의 높이가 자동으로 고려돼요.

**Example: PositionToast**

```tsx
function PositionToast() {
  const toast = useToast();

  return (
    <Button
      onClick={() => {
        toast.openToast("새로운 알림이 있어요", {
          type: "top",
          gap: 30,
        });
      }}
    >
      상단 토스트 열기
    </Button>
  );
}
```

### 애니메이션 타이밍 조절하기

`duration` 속성을 사용하여 토스트 메시지가 표시되는 시간을 밀리초 단위로 조절할 수 있어요.
이 속성은 웹 환경에서만 사용할 수 있어요. 앱 환경에서는 기본값인 3000ms로 고정돼요.

**Example: AnimationTimingToast**

```tsx
function AnimationTimingToast() {
  const toast = useToast();

  return (
    <Button
      onClick={() => {
        toast.openToast("메시지예요", {
          duration: 1000,
        });
      }}
    >
      애니메이션 타이밍을 조절한 토스트 열기
    </Button>
  );
}
```

## 인터페이스

**Type: ToastButton**

```typescript
export interface ToastButton {
  /**
   * `Toast` 컴포넌트의 버튼에 표시될 텍스트에요.
   */
  text: string;

  /**
   * `Toast` 컴포넌트의 버튼을 클릭할 때 실행될 함수에요.
   */
  onClick: () => void;
}
```

**Type: OpenToastOptions**

```typescript
export interface OpenToastOptions {
  /**
   * `Toast` 컴포넌트의 토스트 메시지의 위치를 설정해요.
   *
   * @default 'bottom'
   */
  type?: ToastPosition;

  /**
   * `Toast` 컴포넌트가 표시될 때 상/하단에서 떨어질 간격을 설정해요.
   *
   * 다른 값들보다 우선적으로 적용돼요.
   */
  gap?: number;

  /**
   * `Toast` 컴포넌트에 표시될 아이콘의 이름이에요.
   *
   * lottie와 함께 사용할 수 없어요.
   */
  icon?: string;

  /**
   * `Toast` 컴포넌트에 표시될 아이콘의 모양을 설정해요.
   *
   * @default undefined
   */
  iconType?: "circle" | "square";

  /**
   * `Toast` 컴포넌트에 표시될 로티 애니메이션의 URL이에요.
   *
   * icon과 함께 사용할 수 없어요.
   */
  lottie?: string;

  /**
   * `Toast` 컴포넌트에 표시될 버튼이에요.
   */
  button?: ToastButton;

  /**
   * `BottomCTA` 컴포넌트보다 위에 `Toast` 컴포넌트를 표시할지 설정해요.
   *
   * @default false
   */
  higherThanCTA?: boolean;

  /**
   * `Toast` 컴포넌트가 자동으로 사라질 때까지의 시간(ms)이에요.
   *
   * 버튼이 있는 경우 기본값은 5000ms, 없는 경우 3000ms이에요.
   */
  duration?: number;
}
```

---

# @toss-design-system에서 마이그레이션 (/tds-mobile/migration/from-toss-design-system/)

# @toss-design-system에서 마이그레이션

> **Deprecation Notice**
>
> `@toss-design-system/*` scope의 패키지들은 더 이상 지원되지 않습니다.
> 해당 scope에 대한 npm 권한은 회수되었으며, 앞으로 새로운 버전이 배포되지 않습니다.
>
> 모든 사용자는 `@toss/tds-*` scope의 패키지로 마이그레이션해야 합니다.

## 개요

기존 `@toss-design-system/*` 패키지를 사용하고 계셨다면, `@toss/tds-*` 패키지로 마이그레이션해야 합니다.
이 가이드에서는 자동화된 CLI 도구를 사용하여 쉽게 마이그레이션하는 방법을 안내합니다.

## 패키지 매핑

다음은 기존 패키지와 새 패키지 간의 매핑입니다:

| 기존 패키지                            | 새 패키지                    | 버전 |
| -------------------------------------- | ---------------------------- | ---- |
| `@toss-design-system/colors`           | `@toss/tds-colors`           | ^0   |
| `@toss-design-system/css-utils`        | `@toss/tds-css-utils`        | ^0   |
| `@toss-design-system/typography`       | `@toss/tds-typography`       | ^0   |
| `@toss-design-system/color-utils`      | `@toss/tds-color-utils`      | ^0   |
| `@toss-design-system/spring-easing`    | `@toss/tds-spring-easing`    | ^0   |
| `@toss-design-system/easings`          | `@toss/tds-easings`          | ^0   |
| `@toss-design-system/react-native`     | `@toss/tds-react-native`     | ^1   |
| `@toss-design-system/mobile`           | `@toss/tds-mobile`           | ^2   |
| `@toss-design-system/mobile-bedrock`   | `@toss/tds-mobile-ait`       | ^1   |
| `@toss-design-system/mobile-migration` | `@toss/tds-mobile-migration` | ^2   |

## CLI를 활용한 자동 마이그레이션

`@toss/tds-migration` CLI 도구를 사용하면 import path와 package.json dependencies를 자동으로 변환할 수 있습니다.

<Steps>

### 마이그레이션 CLI 설치

<Tabs items={['pnpm', 'yarn', 'npm']}>
<Tabs.Tab>
`sh
    pnpm add -D @toss/tds-migration
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn add -D @toss/tds-migration
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    npm install -D @toss/tds-migration
    `
</Tabs.Tab>
</Tabs>

### Import Path 마이그레이션

TypeScript/TSX 파일의 import path를 자동으로 변환합니다.

<Tabs items={['pnpm', 'yarn', 'npx']}>
<Tabs.Tab>
`sh
    pnpm exec tds-migrate imports --path "src/**/*.{ts,tsx}"
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn tds-migrate imports --path "src/**/*.{ts,tsx}"
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    npx tds-migrate imports --path "src/**/*.{ts,tsx}"
    `
</Tabs.Tab>
</Tabs>

**변환 예시:**

```diff
- import { colors } from '@toss-design-system/colors';
- import { TDSMobile } from '@toss-design-system/mobile';
+ import { colors } from '@toss/tds-colors';
+ import { TDSMobile } from '@toss/tds-mobile';
```

### package.json Dependencies 마이그레이션

package.json의 dependencies를 자동으로 변환합니다.

<Tabs items={['pnpm', 'yarn', 'npx']}>
<Tabs.Tab>
`sh
    pnpm exec tds-migrate deps --path "**/package.json"
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn tds-migrate deps --path "**/package.json"
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    npx tds-migrate deps --path "**/package.json"
    `
</Tabs.Tab>
</Tabs>

**변환 예시:**

```diff
{
  "dependencies": {
-   "@toss-design-system/colors": "0.1.0",
-   "@toss-design-system/mobile": "2.1.0"
+   "@toss/tds-colors": "^0",
+   "@toss/tds-mobile": "^2"
  }
}
```

### 전체 마이그레이션 (한 번에 실행)

`import path`와 `package.json`을 모두 마이그레이션합니다.

<Tabs items={['pnpm', 'yarn', 'npx']}>
<Tabs.Tab>
`sh
    pnpm exec tds-migrate all --path "."
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn tds-migrate all --path "."
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    npx tds-migrate all --path "."
    `
</Tabs.Tab>
</Tabs>

### 패키지 재설치

마이그레이션 후 패키지를 다시 설치합니다.

<Tabs items={['pnpm', 'yarn', 'npm']}>
<Tabs.Tab>
`sh
    pnpm install
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn install
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    npm install
    `
</Tabs.Tab>
</Tabs>

</Steps>

## CLI 옵션

| 옵션                | 설명                               | 기본값                              |
| ------------------- | ---------------------------------- | ----------------------------------- |
| `-p, --path <path>` | 마이그레이션 대상 경로 (glob 패턴) | `**/*.{ts,tsx}` / `**/package.json` |
| `--tsconfig <path>` | tsconfig.json 경로                 | `tsconfig.json`                     |
| `--dry-run`         | 변경 없이 미리보기만               | `false`                             |

### Dry-run 모드

실제 변경 전에 어떤 파일이 변경될지 미리 확인할 수 있습니다.

```sh
npx tds-migrate imports --path "src/**/*.{ts,tsx}" --dry-run
```

## 수동 마이그레이션

CLI 도구 대신 수동으로 마이그레이션하려면 다음 단계를 따르세요:

### 1. 새 패키지 설치

<Tabs items={['pnpm', 'yarn', 'npm']}>
<Tabs.Tab>
`sh
    pnpm add @toss/tds-mobile@^2
    pnpm remove @toss-design-system/mobile
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn add @toss/tds-mobile@^2
    yarn remove @toss-design-system/mobile
    `
</Tabs.Tab>
<Tabs.Tab>
`sh
    npm install @toss/tds-mobile@^2
    npm uninstall @toss-design-system/mobile
    `
</Tabs.Tab>
</Tabs>

### 2. Import 경로 변경

IDE의 전역 검색 및 바꾸기 기능을 사용하여 import 경로를 변경합니다.

```diff
- import { Button } from '@toss-design-system/mobile';
+ import { Button } from '@toss/tds-mobile';
```

## 주의사항

> **mobile-bedrock → mobile-ait 변경**
>
> `@toss-design-system/mobile-bedrock` 패키지는 `@toss/tds-mobile-ait`로 변경되었습니다.
> 패키지 이름만 변경된 것이 아니라, Provider 이름도 변경되었습니다.
>
> CLI는 import 문과 JSX 엘리먼트를 모두 자동으로 변경합니다:
>
> ```diff
>
> ```

- import { TDSMobileBedrockProvider } from '@toss-design-system/mobile-bedrock';

* import { TDSMobileAITProvider } from '@toss/tds-mobile-ait';

- <TDSMobileBedrockProvider>

* <TDSMobileAITProvider>
    {/* ... */}

- </TDSMobileBedrockProvider>

* </TDSMobileAITProvider>

````

## 문의

마이그레이션 중 문제가 발생하거나 문의사항이 있으시면 앱인토스 커뮤니티로 연락해 주세요.

---

# Migrate to v2.x (/tds-mobile/migration/v2/)

# Migrate to v2.x

`@toss/tds-mobile` v1.x에서 v2.x로 마이그레이션을 하는 방법을 설명해요.

## 이 가이드가 끝나면

1. **major 버전업**
 `@toss/tds-mobile@^2.0.0`이 설치돼요.
2. **BREAKING CHANGE를 마이그레이션해요**
 컴포넌트 이름 변경, prop 이름 변경 등의 변경사항을 자동으로 처리해요.
3. **일관성 있는 API**
 더욱 직관적이고 일관성 있는 컴포넌트 API를 사용할 수 있어요.

## 변경사항 요약

| 컴포넌트                      | 변경 내용                                                                                                                                              | 예시                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------- |
| `Badge`                       | `type` → `color`<br/>`style` → `variant`<br/>`htmlStyle` → `style`                                                                                     | `` |
| `BoardRow`                    | `RightArrow` → `ArrowIcon`                                                                                                                             | ``                                   |
| `BottomCTA`, `FixedBottomCTA` | `TypeA` → `Single`<br/>`TypeB` → `Double`                                                                                                              | ``, ``             |
| `Button`                      | `size` 값 변경<br/>(`tiny` → `small`, `big` → `xlarge`)<br/>`type` → `color`<br/>`style` → `variant`<br/>`htmlType` → `type`<br/>`htmlStyle` → `style` | `` |
| `IconButton`                  | `label` → `aria-label`                                                                                                                                 | ``                         |
| `ListRow`                     | `verticalPadding` 값 변경                                                                                                                              | ``                     |
| `TextButton`                  | `typography` → `size`                                                                                                                                  | ``                             |
| `Top`                         | `subtitle1` → `subtitleTop` <br/> `subtitle2` → `subtitleBottom`                                                                                       | ``                                |

## CLI를 활용한 마이그레이션

이번 마이그레이션에서는 직접 v2로 버전업을 해주셔야 해요.
upgrade 명령어가 아닌`^2` 버전으로 설치하셔도 괜찮아요.

<Tabs items={['pnpm', 'yarn']}>
<Tabs.Tab>
  ```sh
  pnpm up "@toss/tds-mobile*"
  ```

</Tabs.Tab>
<Tabs.Tab>
  ```sh
  yarn upgrade "@toss/tds-mobile*"
  ```
</Tabs.Tab>
</Tabs>

기존에 사용했던 `TDSMobileBedrockProvider`를 `TDSMobileAITProvider`로 변경할 수 있도록 패키지를 다시 설치해주세요.

<details>
<summary>AITProvider, 어떤 것이 변경되나요?</summary>
<div className="nx-p-2">
  우선, `"@apps-in-toss/web-framework": ">=0.0.31"`으로 peer가 업데이트 돼요. 또한 `Bedrock`이라는 이름을 통해 web으로
  개발하시는 분들에게 불필요한 context 및 러닝커브를 전달할 필요가 없도록 AITProvider로 변경했어요. 또한, 이제 버튼
  색상들을 일괄로 변경할 수 있도록 brandColor를 주입 받는 것 또한 가능해요. bedrock.config.ts에 명시한 primaryColor가
  버튼의 배경색으로 일괄 변경됩니다.
</div>
</details>

<Tabs items={['pnpm', 'yarn']}>
<Tabs.Tab>
  ```sh
  pnpm install @toss/tds-mobile-ait
  pnpm remove @toss/tds-mobile-bedrock
  ```

</Tabs.Tab>
<Tabs.Tab>
  ```sh
  yarn add @toss/tds-mobile-ait
  yarn remove @toss/tds-mobile-bedrock
  ```
</Tabs.Tab>
<Tabs.Tab>
  ```sh
  npm install @toss/tds-mobile-ait
  npm uninstall @toss/tds-mobile-bedrock
  ```
</Tabs.Tab>
</Tabs>

<Tabs items={['pnpm', 'yarn']}>
<Tabs.Tab>

  ```sh
  pnpm exec @toss/tds-mobile-migration tds-v2 --glob="{src,pages}/**/*{tsx,ts}"
  ```

</Tabs.Tab>
<Tabs.Tab>
  ```sh
  yarn dlx @toss/tds-mobile-migration tds-v2 --glob="{src,pages}/**/*{tsx,ts}"
  ```
</Tabs.Tab>
</Tabs>

`glob` 옵션에는 마이그레이션할 파일 경로를 *glob pattern*으로 입력해주세요. 기본 값은 `'{src,pages}/**/*.{ts,tsx}'`예요.

### CLI 마이그레이션 제한사항

> **로컬 래핑 컴포넌트는 자동 마이그레이션 대상에 포함되지 않아요!** Badge, Button 등 prop이 변경된 컴포넌트를
>   wrapping해서 만든 local 컴포넌트는 이번 migration CLI의 대상에 포함되지 않아요. 마이그레이션 간에 유의해주세요.

#### 예시: 자동 마이그레이션되지 않는 케이스

```tsx
import type { ComponentProps } from 'react';
import { Button } from '@toss/tds-mobile';

// 로컬 래핑 컴포넌트
export const MyButton = (props: ComponentProps<typeof Button>) => {
return <Button {...props} />;
};

// 사용하는 곳 - ❌ 이런 케이스는 CLI에서 변환되지 않아요
function SomeComponent() {
return (
  <MyButton
    type="primary"            {/* ❌ color로 변환되지 않음 */}
    style="filled"            {/* ❌ variant로 변환되지 않음 */}
    htmlStyle={{ margin: 4 }} {/* ❌ style로 변환되지 않음 */}
  >
    버튼
  </MyButton>
);
}
````

#### 수동 처리 방법

로컬 래핑 컴포넌트를 사용하는 경우, 해당 컴포넌트의 변경사항을 참고해서 수동으로 처리해주세요:

<Cards>

</Cards>

```tsx
// 수동으로 prop 이름을 변경해주세요
function SomeComponent() {
  return (
    <MyButton
      color="primary"          {/* ✅ type → color */}
      variant="filled"         {/* ✅ style → variant */}
      style={{ margin: 4 }}    {/* ✅ htmlStyle → style */}
    >
      버튼
    </MyButton>
  );
}
```

## 수동 마이그레이션 가이드

> 이 아래부터는 수동으로 마이그레이션을 하시는 분을 위해 제공되는 문서예요.

### 패키지 업데이트

다음 커맨드로 패키지를 업데이트해주세요.

<Tabs items={['pnpm', 'yarn']}>
<Tabs.Tab>
`sh
    pnpm up "@toss/tds-mobile*"
    `

</Tabs.Tab>
<Tabs.Tab>
`sh
    yarn upgrade "@toss/tds-mobile*"
    `
</Tabs.Tab>
</Tabs>

### Badge

속성명이 변경되었어요.

1. **type → color**

   ```diff /type/ /color/
   -<Badge type="blue" style="filled">배지</Badge>
   +<Badge color="blue" variant="filled">배지</Badge>

   -<Badge type="teal" style="outlined">배지</Badge>
   +<Badge color="teal" variant="outlined">배지</Badge>
   ```

2. **style → variant**

   ```diff /style/ /variant/
   -<Badge style="fill">배지</Badge>
   +<Badge variant="fill">배지</Badge>

   -<Badge style="weak">배지</Badge>
   +<Badge variant="weak">배지</Badge>
   ```

3. **htmlStyle → style**

   > 이제 `style` prop이 `variant`로 바뀌었으므로, HTML style을 위한 `htmlStyle`을 다시 `style`로 변경해야해요.

   ```diff /htmlStyle/ /style/
   -<Badge htmlStyle={{ backgroundColor: 'red' }}>HTML 스타일 배지</Badge>
   +<Badge style={{ backgroundColor: 'red' }}>HTML 스타일 배지</Badge>
   ```

4. **Paragraph.Badge, Top.SubtitleBadges에도 동일하게 적용**

   ```diff /type/ /color/ /style/ /variant/
   -<Paragraph.Badge type="yellow" style="fill">경고</Paragraph.Badge>
   +<Paragraph.Badge color="yellow" variant="fill">경고</Paragraph.Badge>

   -<Top.SubtitleBadges type="elephant" style="weak">정보</Top.SubtitleBadges>
   +<Top.SubtitleBadges color="elephant" variant="weak">정보</Top.SubtitleBadges>
   ```

### BoardRow

속성명이 변경되었어요.

1. **BoardRow.RightArrow → BoardRow.ArrowIcon**

   ```diff /RightArrow/ /ArrowIcon/
   -<BoardRow.RightArrow />
   +<BoardRow.ArrowIcon />
   ```

   ```diff /BoardRowRightArrowProps/ /BoardRowArrowIconProps/
   -import type { BoardRowRightArrowProps } from '@toss/tds-mobile';
   +import type { BoardRowArrowIconProps } from '@toss/tds-mobile';
   ```

### BottomCTA / FixedBottomCTA

SubComponent 이름이 변경되었어요.

1. **TypeA → Single**

   ```diff /TypeA/ /Single/
   -<BottomCTA.TypeA onClick={handleClick}>단일 버튼</BottomCTA.TypeA>
   +<BottomCTA.Single onClick={handleClick}>단일 버튼</BottomCTA.Single>

   -<FixedBottomCTA.TypeA onClick={handleClick}>고정 단일 버튼</FixedBottomCTA.TypeA>
   +<FixedBottomCTA.Single onClick={handleClick}>고정 단일 버튼</FixedBottomCTA.Single>
   ```

2. **TypeB → Double**

   ```diff /TypeB/ /Double/
   -<BottomCTA.TypeB
   +<BottomCTA.Double
     leftButton={<CTAButton color="secondary">취소</CTAButton>}
     rightButton={<CTAButton color="primary">확인</CTAButton>}
   />

   -<FixedBottomCTA.TypeB
   +<FixedBottomCTA.Double
     leftButton={<CTAButton color="secondary">취소</CTAButton>}
     rightButton={<CTAButton color="primary">확인</CTAButton>}
   />
   ```

### Button

속성명이 변경되었어요.

1. **type → color**

   ```diff /type/ /color/
   -<Button type="primary">버튼</Button>
   +<Button color="primary">버튼</Button>

   -<Button type="secondary">버튼</Button>
   +<Button color="secondary">버튼</Button>
   ```

2. **style → variant**

   ```diff /style/ /variant/
   -<Button style="filled">버튼</Button>
   +<Button variant="filled">버튼</Button>

   -<Button style="outlined">버튼</Button>
   +<Button variant="outlined">버튼</Button>
   ```

3. **htmlType → type**

   ```diff /htmlType/ /type/
   -<Button htmlType="submit">폼 버튼</Button>
   +<Button type="submit">폼 버튼</Button>
   ```

4. **htmlStyle → style**

   ```diff /htmlStyle/ /style/
   -<Button htmlStyle={{ margin: '10px' }}>스타일 버튼</Button>
   +<Button style={{ margin: '10px' }}>스타일 버튼</Button>
   ```

5. **size 값 매핑 변경**

   T-Shirts 사이즈 prop value로 일관되게 변경했어요.

   | 1.x  | 2.x    |
   | ---- | ------ |
   | tiny | small  |
   | big  | xlarge |

   ```diff /tiny/ /small/ /big/ /xlarge/
   -<Button size="tiny">작은 버튼</Button>
   +<Button size="small">작은 버튼</Button>

   -<Button size="big">큰 버튼</Button>
   +<Button size="xlarge">큰 버튼</Button>
   ```

6. **Button 컴포넌트를 확장해 사용하는 다른 컴포넌트들에게도 동일하게 적용**

   **직접 Button을 확장하는 컴포넌트:**

   - `ResultButton`
   - `CTAButton`
   - `FixedBottomCTA`
   - `BottomCTA`

   **Button 기반 컴파운드 컴포넌트:**

   - `BottomCTA.Single`
   - `BottomCTA.Double`
   - `FixedBottomCTA.Double`
   - `BottomSheet.CTA`
   - `BottomSheet.DoubleCTA`
   - `ConfirmDialog.ConfirmButton`
   - `ConfirmDialog.CancelButton`
   - `Top.LowerButton`
   - `Top.RightButton`
   - `Top.LowerCTAButton`

   ```diff /type/ /color/ /style/ /variant/ /tiny/ /small/ /big/ /xlarge/
   -<AlertDialog.AlertButton type="primary" style="filled" size="tiny">작은 알럿 버튼</AlertDialog.AlertButton>
   +<AlertDialog.AlertButton color="primary" variant="filled" size="small">작은 알럿 버튼</AlertDialog.AlertButton>

   -<AlertDialog.AlertButton type="secondary" style="outlined" size="big">큰 알럿 버튼</AlertDialog.AlertButton>
   +<AlertDialog.AlertButton color="secondary" variant="outlined" size="xlarge">큰 알럿 버튼</AlertDialog.AlertButton>
   ```

### IconButton

속성명이 변경되었어요.

1. **label → aria-label**

   > `aria-label` prop은 IconButton 컴포넌트에서 필수 값이에요. 사용자에게 전달되는 시각적 텍스트가 없는 IconButton의

>      경우 `aria-label`이 역할을 전달하는 역할이 됩니다. 마이그레이션 편의를 위해 이번 마이그레이션에서는 빈 값으로
>      마이그레이션 됩니다.

```diff /label/ /aria-label/
-<IconButton label="닫기" />
+<IconButton aria-label="닫기" />
```

```diff /label/ /aria-label/
-<ListRow.IconButton label="설정" />
+<ListRow.IconButton aria-label="설정" />
```

### ListRow

값이 최신화되었어요.

| 1.x          | 2.x    |
| ------------ | ------ |
| extraSmall   | small  |
| extraSmall-8 | small  |
| small        | medium |
| small-16     | medium |
| medium       | large  |
| medium-24    | large  |
| large        | xlarge |
| large-32     | xlarge |

1. **verticalPadding 값 매핑 변경**

   ```diff /extraSmall/ /small/ /medium/ /large/ /xlarge/
   -<ListRow verticalPadding="extraSmall">가장 작은 패딩</ListRow>
   +<ListRow verticalPadding="small">가장 작은 패딩</ListRow>

   -<ListRow verticalPadding="small">작은 패딩</ListRow>
   +<ListRow verticalPadding="medium">작은 패딩</ListRow>

   -<ListRow verticalPadding="medium">중간 패딩</ListRow>
   +<ListRow verticalPadding="large">중간 패딩</ListRow>

   -<ListRow verticalPadding="large">큰 패딩</ListRow>
   +<ListRow verticalPadding="xlarge">큰 패딩</ListRow>
   ```

2. **숫자 접미사가 있는 값들도 동일하게 매핑**

   ```diff /extraSmall-8/ /small-16/ /medium-24/ /large-32/ /small/ /medium/ /large/ /xlarge/
   -<ListRow verticalPadding="extraSmall-8">8px 패딩</ListRow>
   +<ListRow verticalPadding="small">8px 패딩</ListRow>

   -<ListRow verticalPadding="small-16">16px 패딩</ListRow>
   +<ListRow verticalPadding="medium">16px 패딩</ListRow>

   -<ListRow verticalPadding="medium-24">24px 패딩</ListRow>
   +<ListRow verticalPadding="large">24px 패딩</ListRow>

   -<ListRow verticalPadding="large-32">32px 패딩</ListRow>
   +<ListRow verticalPadding="xlarge">32px 패딩</ListRow>
   ```

   > 숫자 접미사(`-8`, `-16`, `-24`, `-32`)가 있는 값들도 기본 값과 동일하게 매핑돼요.

### TextButton

속성명이 변경되었어요.

1. **typography → size**

   | 1.x (typography) | 2.x (size) |
   | ---------------- | ---------- |
   | t7               | xsmall     |
   | t6               | small      |
   | t5               | medium     |
   | t4               | large      |
   | t3               | xlarge     |
   | st2              | xxlarge    |

   ```diff /typography/ /size/ /t7/ /t6/ /t5/ /t4/ /t3/ /st2/ /xsmall/ /small/ /medium/ /large/ /xlarge/ /xxlarge/
   -<TextButton typography="t7">아주 작은 버튼</TextButton>
   +<TextButton size="xsmall">아주 작은 버튼</TextButton>

   -<TextButton typography="t6">작은 버튼</TextButton>
   +<TextButton size="small">작은 버튼</TextButton>

   -<TextButton typography="t5">중간 버튼</TextButton>
   +<TextButton size="medium">중간 버튼</TextButton>

   -<TextButton typography="t4">큰 버튼</TextButton>
   +<TextButton size="large">큰 버튼</TextButton>

   -<TextButton typography="t3">아주 큰 버튼</TextButton>
   +<TextButton size="xlarge">아주 큰 버튼</TextButton>

   -<TextButton typography="st2">엄청 큰 버튼</TextButton>
   +<TextButton size="xxlarge">엄청 큰 버튼</TextButton>
   ```

   > `typography` prop이 `size` prop으로 변경되고, 값은 자동으로 매핑돼요.

2. **ListHeader, Top, AlertDialog의 TextButton 관련 컴포넌트도 동일하게 적용**

   ```diff /typography/ /size/ /t7/ /t6/ /xsmall/ /small/
   -<ListHeader.TitleTextButton typography="t7">작은 헤더</ListHeader.TitleTextButton>
   +<ListHeader.TitleTextButton size="xsmall">작은 헤더</ListHeader.TitleTextButton>

   -<Top.SubtitleTextButton typography="t6">부제목 버튼</Top.SubtitleTextButton>
   +<Top.SubtitleTextButton size="small">부제목 버튼</Top.SubtitleTextButton>

   -<AlertDialog.AlertButton typography="t6">확인</AlertDialog.AlertButton>
   +<AlertDialog.AlertButton size="small">확인</AlertDialog.AlertButton>
   ```

### Top

속성명이 변경되었어요.

1. **subtitle1 → subtitleTop**

   ```diff /subtitle1/ /subtitleTop/
   -<Top subtitle1="상단 부제목">메인 제목</Top>
   +<Top subtitleTop="상단 부제목">메인 제목</Top>
   ```

2. **subtitle2 → subtitleBottom**

   ```diff /subtitle2/ /subtitleBottom/
   -<Top subtitle2="하단 부제목">메인 제목</Top>
   +<Top subtitleBottom="하단 부제목">메인 제목</Top>
   ```

3. **두 개의 subtitle을 함께 사용하는 경우**

   ```diff /subtitle1/ /subtitle2/ /subtitleTop/ /subtitleBottom/
   -<Top subtitle1="상단 부제목" subtitle2="하단 부제목">메인 제목</Top>
   +<Top subtitleTop="상단 부제목" subtitleBottom="하단 부제목">메인 제목</Top>
   ```

---

> 마이그레이션 간 발생한 문제 또는 문의사항은 앱인토스 커뮤니티로 문의 부탁드려요.

---

# Start (/tds-mobile/start/)

## TDS Mobile 시작하기

TDS Mobile 패키지를 사용하면 모바일 환경에서 다양한 UI 컴포넌트를 쉽게 적용할 수 있어요. 이 문서에서는 TDS Mobile을 프로젝트에 설치하고 사용하는 방법을 알려드려요.

### 1. 필수 패키지 설치하기

먼저, TDS Mobile을 사용하려면 관련된 패키지들을 설치해야 해요.

```sh npm2yarn
npm install @toss/tds-mobile @toss/tds-mobile-ait @emotion/react@^11 react@^18 react-dom@^18
```

### 2. Provider 설정하기

TDS Mobile을 사용하려면, 프로젝트의 최상위를 `TDSMobileAITProvider`로 감싸야 해요. 이 컴포넌트는 TDS Mobile의 컴포넌트들이 올바르게 동작할 수 있도록 설정해 줘요.

```jsx copy
import { TDSMobileAITProvider } from "@toss/tds-mobile-ait";

function App({ Component, pageProps }) {
  return (
    <TDSMobileAITProvider>
      <Component {...pageProps} />
    </TDSMobileAITProvider>
  );
}
```

### 3. 사용하기

패키지 설치와 설정이 끝났다면, 이제 컴포넌트를 프로젝트에 불러와서 사용할 수 있어요. 예를 들어, `Button` 컴포넌트를 사용하려면 다음과 같이 코드를 작성하면 돼요.

```js copy
import { Button } from "@toss/tds-mobile";

const App = () => <Button>버튼</Button>;
```
