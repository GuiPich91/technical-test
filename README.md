# Technical test

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug :

- Sign up to the app
- Create at least 2 others users on people page ( not with signup )
- Edit these profiles and add aditional information
- Create a project
- Input some information about the project
- Input some activities to track your work in the good project

Then, see what happens in the app and fix the bug you found doing that.

## Then

Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions :

- What bugs did you find ? How did you solve these and why ?
- Which feature did you develop and why ?
- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ?

To signin:
i delete the trim.lowercase to signin in api/auth :

To signup :
I add the type="password" to the password Input,

To create a new people :

app Part :
i delete the disabled on the name input in user/view.js :

<!-- <input
    className="projectsInput text-[14px] font-normal text-[#212325] bg-[#F9FBFD] rounded-[10px]"
    name="name"
    value={values.name}
    onChange={handleChange}
/> -->

i change the name input to name instead of username in user/list.js :

 <!-- <input className="projectsInput text-[14px] font-normal text-[#212325] rounded-[10px]" name="name" value={values.username} onChange={handleChange} /> -->

I change the onChange Hook to onClick to update the user :

<!-- <LoadingButton className="bg-[#0560FD] text-[16px] font-medium text-[#FFFFFF] py-[12px] px-[22px] rounded-[10px]" loading={isSubmitting} onClick={handleSubmit}>
Update
</LoadingButton> -->

api Part :
i change query.user = req.query.userId by query.userId = req.query.userId

<!-- router.get("/", passport.authenticate("user", { session: false }), async (req, res) => {
  try {
    const query = {};
    console.log(req.query);
    if (req.query.userId) query.userId = req.query.userId; -->

Project:
api part : change find to findOne to don't get an array

<!-- router.get("/:id", passport.authenticate("user", { session: false }), async (req, res) => {
  try {
    const data = await ProjectObject.findOne({ _id: req.params.id });
    return res.status(200).send({ ok: true, data });
  } catch (error) {
    console.log(error);
    res.status(500).send({ ok: false, code: SERVER_ERROR, error });
  }
}); -->

i remove the disabled label on the name input :

<!-- <div className="w-full md:w-[260px] mt-2">
    <div className="text-[14px] text-[#212325] font-medium	">Name of project</div>
    <input className="projectsInput text-[14px] font-normal text-[#212325] rounded-[10px]" name="name" value={values.name} onChange={handleChange} />
</div> -->

I fix the searchbar in project/list.js

 <!-- useEffect(() => {
    (async () => {
      const { data: u } = await api.get("/project");
      setProjects(u);
    })();
  }, []);

  useEffect(() => {
    if (!projects) return;
    setProjectsFiltered(
      projects
        .filter((u) => !filter?.status || u.status === filter?.status)
        .filter((u) => !filter?.search || u.name.toLowerCase().includes(filter?.search.toLowerCase())),
      );
      console.log(projectsFiltered);
  }, [projects, filter]); -->

Activities :

I modified the selectProject component and the activity/index.js to have the possibility to select one project and see the activity of it

New Features :

I create a filter in project List to see inactif/actif project :

 <!-- <FilterStatus filter={filter} setFilter={setFilter} /> -->

i add a table in User to see his project and activity

# Feedback

## Bug fix

Good job, most of the bug as been fixed with the best solution

## New Feature

Nice idea and well exectuted : no need to remake everything, a copy paste of the existing is good enough. Well done

## General feedback

All good, only careful with the console.log everywhere, nice to debug but to remove when doing a PR
