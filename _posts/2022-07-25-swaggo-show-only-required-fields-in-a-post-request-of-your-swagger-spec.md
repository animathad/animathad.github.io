---
title: "Swaggo: Show only required fields in a Post Request of your swagger spec"
tags: [gin, go, rest api, swagger, swaggo]
description: "I have a struct type Person struct { Name string `json:”name” Email string `json:”email” Occupation string `json:”occupation” } This is being used by a…"
original_date: 2022-07-25T13:33:49-07:00
---

<https://github.com/swaggo/swag/issues/123>

I have a struct

```
type Person struct {
 Name string `json:"name"
 Email string `json:"email"
 Occupation string `json:"occupation" 
}
```

This is being used by a route to generate a swagger spec

```
// HandlePostPerson godoc
// @Summary Create a Person
// @Description Create a Person
// @Accept json
// @Produce json
// @Param person body Person true "A Person"
// @Router /person [post]
func (personHandler *PersonHandler) HandlePostPerson(c *gin.Context) {
...
}
```

This will make **all** the fields in the Person struct as required in the Swagger Spec.

**Ignore fields in the swagger**

If you are ok ignoring `Email` in the Request, then you have to do this:

```
type Person struct {
 Name string `json:"name" validate:"required"`
 Email string `json:"email"`
 Occupation string `json:"occupation" validate:"required"`
}
```

This will make the `Name` & `Occupation` as required in your Swagger spec i.e. comes with `*`
