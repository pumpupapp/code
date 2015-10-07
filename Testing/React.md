# React Testing



```jsx
describe('<MyComponent />', () => {

  // ...

})
```


## Props & State



```jsx
describe('.propTypes', () => {


  // Exact prop type
  describe('.isInShareMode', () => {

    it('is a boolean', () => {
      Widget.propTypes.isInShareMode.should.be.exactly(React.PropTypes.bool)
    })

  })



  // Function prop type (eg. React.PropTypes.oneOf)
  describe('.type', () => {

    it('validates the widget type', () => {
      true.should.eql(Widget.propTypes.type({ type: WIDGET.TYPE.WEIGHT }, 'type') == null)
      true.should.eql(Widget.propTypes.type({ type: WIDGET.TYPE.ACTIVITIES }, 'type') == null)
      Widget.propTypes.type({ type: -1 }).should.be.an.instanceOf(Error)
    })

  })


})



describe('::getInitialState', () => {

  it('returns the initial state', () => {

    let type = WIDGET.TYPE.WEIGHT
    let widgetComponent = TestUtils.renderIntoDocument(
      <Widget type={type} />
    )
    widgetComponent.getInitialState().should.eql({
      isInShareMode : false,
    })

  })

})
```





## Renderings



```jsx
describe('::render', () => {

  it('renders the widget', () => {

    // Render the weight widget
    let widgetComponent = TestUtils.renderIntoDocument(
      <Widget type={WIDGET.TYPE.WEIGHT} />
    )

    // Ensure it was rendered properly
    let weightWidgetNode = widgetComponent.getDOMNode()
    weightWidgetNode.className.should.eql('widget')
    weightWidgetNode.attributes.getNamedItem('data-ui-theme').value
      .should.eql(WIDGET.THEME[WIDGET.TYPE.WEIGHT])

    // Spy on nested render calls
    let renderModalSpy = sinon.spy(widgetComponent, 'renderModal')

    // Run render
    widgetComponent.render()

    // Ensure the nested render calls were made
    renderModalSpy.callCount.should.eql(1)

  })

})
```


This example demonstrates how to test nested elements.

```jsx
describe('::renderActivitiesList', () => {

  it('returns the activities list', () => {

    // Render the original component, then call the nested render function
    let type                  = WIDGET.TYPE.ACTIVITIES
    let widgetComponent         = TestUtils.renderIntoDocument(<Widget type={type} />)
    let activitiesListComponent = TestUtils.renderIntoDocument(widgetComponent.renderActivitiesList())

    // Test that the component uses the correct constructor
    true.should.eql(activitiesListComponent.constructor === AppBody.Block)
    activitiesListComponent.props.isFullWidth.should.eql(true)

    // Test that the only child element is of the right type
    React.Children.count(activitiesListComponent.props.children).should.eql(1)
    let activityLogListElement = activitiesListComponent.props.children
    TestUtils.isElementOfType(activityLogListElement, ActivityLogList).should.eql(true)

    // Test that the grandchildren are rendered properly
    React.Children.count(activityLogListElement.props.children).should.eql(2)
    React.Children.forEach(activityLogListElement.props.children, (activityLogListItemElement, i) => {
      React.Children.count(activityLogListItemElement.props.children).should.eql(0)
      TestUtils.isElementOfType(activityLogListItemElement, ActivityLogList.Item).should.eql(true)
      activityLogListItemElement.props.activityLog.should.be.exactly(
        widgetComponent.state.recentActivityLogs[i])
    })

  })

})
```


If the element only has a text node child
```jsx
baseButtonElement.props.children.should.eql('See All')
```




Other component tests are trivial.