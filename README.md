<h1>JRG</h1>
<br/>
<span>Simple DSL which is used to generate Java SpringBoot and React.js project. Precisely, it generates repositoires, services, controllers, models and dtos for backend and navbar, preview page, popup, interfaces, services and models for frontend.</span>
<br/>
<h3>Language grammar</h3>
<ul>
  <li>
    Each entity must start with reserved word <b>entity</b> and name must be
    <b>capitalized</b>
  </li>
  <li>Entity name must be capitalized</li>
  <li>Entity can't contain multiple properties of same entity type</li>
  <li>
    Properties, format(<b>name : type</b>), can be
    <b>Constraint</b> or <b>Relational</b>
  </li>
  <li>Property name can't be <b>id</b></li>
  <li>Property name must be uncapitalized</li>
  <li>Property can't be of a type as its containing entity</li>
  <li>
    Constraint properties can be of type:
    <ul>
      <li><b>int</b></li>
      <li><b>float</b></li>
      <li><b>string</b></li>
      <li><b>bool</b></li>
    </ul>
  </li>
  <li>
    And can be of a collection type:
    <ul>
      <li><b>List</b></li>
      <li><b>Set</b></li>
    </ul>
  </li>
  <li>
    Properties of constraint type can have following constraints:
    <ul>
      <li><b>Unique</b></li>
      <li><b>NotNullable</b></li>
      <li><b>Length, format(Length = value(int))</b></li>
    </ul>
  </li>
  <li>Length constraint can only be set on a property of type string</li>
  <li>
    Relational properties can be of type of other entities and must be of a
    realtional type:
    <ul>
      <li><b>OneToOne</b></li>
      <li><b>ManyToOne</b></li>
      <li><b>OneToMany</b></li>
      <li><b>ManyToMany</b></li>
    </ul>
  </li>
  <li>OneToMany and ManyToMany must be of collection type</li>
  <li>OneToOne and ManyToOne can't be of collection type</li>
  <li>
    Additional decorators for relational types are:
    <ul>
      <li>
        <b>Fetch</b>, possible values:
        <ul>
          <li><b>LAZY</b></li>
          <li><b>EAGER</b></li>
        </ul>
      </li>
      <li>
        <b>Cascade</b>, possible values:
        <ul>
          <li><b>PERSIST</b></li>
          <li><b>MERGE</b></li>
          <li><b>REMOVE</b></li>
          <li><b>REFRESH</b></li>
          <li><b>DETACH</b></li>
          <li><b>ALL</b></li>
        </ul>
      </li>
    </ul>
  </li>
  <li>Constraints and relational decorators are defined inside <b>[]</b>, and are separated with <b>,</b></li>
  <li>Plural value can be defined, format(<b>plural = "name"</b>)</li>
  <li>Plural value must be capitalized</li>
</ul>
<br/>
<h3>Example</h3>
<br/>

```
entity Dog
	[Length=256]
	name: string
	breed: string
	tramp: bool
	age: int
	weight: float
	[ManyToMany]
	human: List<Human>
	plural = 'Dogs' 
	
entity Human
	[Unique, Length=13]
	jmbg: string
	[Length=256]
        name: string
        [Length=256]
        lastname: string
        [ManyToMany]
        dogs: Set<Dog>
```
