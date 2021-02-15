<script>
  import Form from "./Form.svelte";
  import Header from "./Header.svelte";
  import List from "./List.svelte";

  let list = [
    { text: "txt1", id: 1, state: false },
    { text: "txt2", id: 2, state: false },
    { text: "txt3", id: 3, state: false },
  ];

  function onDeleteHandler(e) {
    const id = e.detail;
    list = list.filter((x) => x.id !== id);
  }
  function onCompleteHandler(e) {
    const id = e.detail;
    list = list.map((x) => {
      if (x.id === id) x.state = true;
      return x;
    });
  }
  function onNewItemHandler(e) {
    let item = e.detail;
    item.id = list.length + 1;

    let tmp = list;
    tmp.push(item);
    list = tmp;
  }
</script>

<div>
  <Form on:newitem={onNewItemHandler} />
  <Header count={list.length} />
  <List
    items={list}
    on:complete={onCompleteHandler}
    on:delete={onDeleteHandler}
  />
</div>

