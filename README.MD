### 테스트 코드의 목적

- 작성한 코드가 예상대로 동작하는지 확인하기 위해
- 코드를 수정했을 때 기존 기능이 깨지지 않는지 확인하기 위해
- 테스트 코드를 보고 이 코드가 어떻게 동작하는지 알 수 있으므로 문서화 기능도 한다. 코드가 복잡하면 보고 이해하는것도 한참 걸리겠지. 하지만 테스트코드에는 이 코드가 어떻게 동작하는지 명시를 해둔다고.

코드를 작성했다. 이 코드가 잘 동작하는지 알아볼 방법은?

- 새로고침? 클릭해보기?
- 테스트 코드를 작성하면 된다.

```jsx
describe("Counter", () => {
  it("renders correctly", () => {
    // 사람 눈에 보이지 않지만 Counter 컴포넌트를 렌더링한다.
    render(<Counter />);
    // Counter 컴포넌트가 제대로 렌더링되었는지 확인한다.
    expect(screen.getByTestId("paragraph")).toHaveTextContent(
      "You clicked 0 times"
    );
  });

  test("버튼 클릭했을 때 반드시 1씩 증가해야 함", () => {
    // 사람 눈에 보이지 않지만 Counter 컴포넌트를 렌더링한다.
    render(<Counter />);
    fireEvent.click(screen.getByText("Click me"));

    // Counter 컴포넌트가 제대로 렌더링되었는지 확인한다.
    expect(screen.getByTestId("paragraph")).toHaveTextContent(
      "You clicked 1 times"
    );
  });
});
```

보면 '선언적'이라는 표현이 떠오른다.
react는 state변경 후의 동작을 작성하고 값을 바꾸면 react가 자동으로 변경사항을 비교하고 돔을 변경한다. 테스트코드도 비슷해 보인다. 기대되는 현상을 정의한 후 동작을 실행하고, 결과를 관측한다.
