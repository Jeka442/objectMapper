
## Description
objectMapper try to map an object properties based on the yup validation provided, if successfuly mapped, the property will be in the exact type, eitherway it will remain the same

isValid function indicates the success result of all "validate" validations

getErrors function returns list of errors if provided

yup here for using yup schemas without the need of import

reset function reset the isValid flag and the errors array

## Usage

```bash
    const temp = {
    name: "jeka",
    age: "5",
    phone: "0526320604",
    city: "holon",
    street: "eilat",
    houseNum: "13"
  };

  const mapObject = () => {
    const { validate, yup, isValid, getErrors } = map();
    const res: Ires = {
      name: validate(temp.name, yup.string().required().max(4), "name-err"),
      age: validate(temp.age, yup.number(), "age-err"),
      phone: validate(temp.phone, yup.string(), "phone-err"),
      address: {
        city: validate(temp.city, yup.string(), "city-err"),
        street: validate(temp.street, yup.string(), "street-err"),
        houseNum: validate(temp.houseNum, yup.number(), "housenum-err")
      }
    };

    if (isValid()) return console.log("yay", res);
    console.log("booo", getErrors());
  };

  mapObject();
```
  
