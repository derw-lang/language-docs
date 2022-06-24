# REPLs

A REPL is an interactive command line program where a user responds to questions and things happen.

There's a package for Derw called [repl](https://github.com/derw-lang/repl), which provides a wrapper around Readline.

The structure is similar to the html package, in that everything revolves around a model-view-update loop.

```elm
import "../derw-packages/derw-lang/repl/src/Repl" exposing (RunningProgram, Program, View, Question, End, Statement, program)

type Page =
    Intro
    | ShowInput
    | Quit

type alias Model = {
    page: Page,
    name: string
}

initialModel: Model
initialModel =
    { page: Intro, name: "" }

type Msg =
    SetName { value: string }
    | Finish

setName: string -> Msg
setName name =
    SetName { value: name }

finish: string -> Msg
finish _ =
    Finish

view: Model -> View Msg
view model =
    case model.page of
        Intro ->
            Question { prompt: "What's your name? ", onInput: setName }
        ShowInput ->
            Question { prompt: `Your name is ${model.name}. Press enter to quit`, onInput: finish }
        Quit ->
            End

update: Msg -> Model -> (Msg -> void) -> Model
update msg model send =
    case msg of
        SetName { value } ->
            { ...model, name: value, page: ShowInput }

        Finish ->
            { ...model, page: Quit }

main: RunningProgram Model Msg
main =
    program { initialModel: initialModel, view: view, update: update }

© 2022 GitHub, Inc. 
```
