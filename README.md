# jsonMarkup

#### Takes JSON, makes markup.

A jQuery plugin for when you need a simple, unopinionated HTML representation of JSON data. Useful for an application where you might need to display or manipulate JSON data.

### Example Use
    
    var jsonData = {
      a: 'b',
      c: [
        {
          d: 'e'
        },
        {
          d: 'f',
          g: 'h'
        }
      ],
      i: {
        j: 'k'
      }
    };

    $('#your-element').jsonMarkup(jsonData);

That's pretty much it. Following the above example, the element with id `your-element` will now contain markup kind of like this: 

    <div class="property-value object-container">
      <div class="property-container" data-path="data.type">
        <span class="property-name">type</span>
        <span class="property-value">disaster</span>
      </div>
      <div class="property-container" data-path="data.time">
        <span class="property-name">time</span>
        <span class="property-value">1</span>
      </div>
      <div class="property-container" data-path="data.total">
        <span class="property-name">total</span>
        <span class="property-value">2622</span>
      </div><div class="property-container" data-path="data.count">
        <span class="property-name">count</span>
        <span class="property-value">10</span>
      </div>
      <div class="property-container" data-path="data.list">
        <span class="property-name">list</span>
        <div class="property-value array-container">
          <div class="property-value object-container">
            <div class="property-container" data-path="data.list.id">
              <span class="property-name">id</span>
              <span class="property-value">13385</span>
            </div>
            <div class="property-container" data-path="data.list.score">
              <span class="property-name">score</span>
              <span class="property-value">1</span>
            </div>
            <div class="property-container" data-path="data.list.fields">
              <span class="property-name">fields</span>
              <div class="property-value object-container">
                <div class="property-container" data-path="data.list.fields.description">
                  <span class="property-name">description</span>
                  <span class="property-value">A total of 43 suspected cases of measles were reported in Malakal County in South Sudan's Upper Nile State since August 2013, according to the Upper Nile State Ministry of Health and WHO. A mass measles vaccination campaign was launched targeting over 31,300 children. ([OCHA, 29 Sep 2013](/node/606536))</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

Each property at every level is wrapped in a `.property-container` element, which contains a `data-path` attribute with the full path to that property in the JSON document. Each `.property-container` holds `.property-name` and `.property-value` elements. Note that `.property-value` elements that represent nested objects or arrays get additional classes (`.object-container` and `.array-container`, respectively). 

Some (very) simple CSS rules might look like this: 

    .property-container {
      margin-left: 15px;
    }

    .property-value {
      margin-left: 10px;
    }

    .property-name {
      font-weight: bold;
    }

    .property-name::after {
      content: ':';
    }