## react-library


## $\textcolor{red}{==> Formik}$


### $\textcolor{blue}{==> What \ is \ Formik \?}$
Formik is a small library that helps you deal with form in react


### $\textcolor{blue}{==> Why \ Formik \?}$
- Managing form data
- Form submission
- Form validation and displaying error messages


useFormik
- initialValues
- onSubmit
  - values
  - reset form


```
import { useFormik } from "formik"

const Form = () => {
  
  const formik = useFormik({
    initialValues : {
      name : '',
      email: '',
      password: ''
    },
    onSubmit : (values, {resetForm})=>{
      console.log(values);
      resetForm({values : ''})
    }
  })
  return (
    <div>
      <form action=""  onSubmit={formik.handleSubmit}>
        <input type="text" name="name" placeholder="name" value={formik.values.name} onChange={formik.handleChange}/><br /><br />
        <input type="email" name="email" placeholder="email" value={formik.values.email} onChange={formik.handleChange}/><br /><br />
        <input type="password" name="password" placeholder="password" value={formik.values.password} onChange={formik.handleChange}/><br /><br />
        <button type="submit">Submit</button>
      </form>
    </div>
  )
}

export default Form

```


## $\textcolor{red}{==> YUP}$
### formik form validation with yup
it is used for react form validation

```
import * as yup from 'yup'

import { useFormik } from "formik"

const Form = () => {
  
  const formik = useFormik({
    initialValues : {
      name : '',
      email: '',
      password: ''
    },
    onSubmit : (values, {resetForm})=>{
      console.log(values);
      resetForm({values : ''})
    },
    validationSchema : yup.object({
      name: yup.string().min(5, 'name must have atleast 5 characters').required(),
      email: yup.string().email().required(),
      password: yup.string().min(8, 'password must have atleast 8 character').required(),
    })
  })
  return (
    <div>
      <form action=""  onSubmit={formik.handleSubmit}>
        <input type="text" name="name" placeholder="name" value={formik.values.name} onChange={formik.handleChange}/><br /><br />
        {formik.touched.name && formik.errors.name && <p style={{ color: 'red' }}>{formik.errors.name}</p>}

        <input type="email" name="email" placeholder="email" value={formik.values.email} onChange={formik.handleChange}/><br /><br />
        {formik.touched.email && formik.errors.email && <p style={{ color: 'red' }}>{formik.errors.email}</p>}

        <input type="password" name="password" placeholder="password" value={formik.values.password} onChange={formik.handleChange}/><br /><br />
        {formik.touched.password && formik.errors.password && <p style={{ color: 'red' }}>{formik.errors.password}</p>}
        <button type="submit">Submit</button>
      </form>
    </div>
  )
}

export default Form

```




















