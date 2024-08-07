<script>
    import Tabs from "../Tabs/Tabs.svelte";
    import KassiTab from "../Tabs/KassiTab.svelte";
    import JeffersonTab from "../Tabs/JeffersonTab.svelte";
    import JointTab from "../Tabs/JointTab.svelte";
    import HouseProjectsTab from "../Tabs/HouseProjectsTab.svelte";
    import IncomeTab from "../Tabs/IncomeTab.svelte";
  
    let items = [
      { label: "Kassi", value: 1, component: KassiTab },
      { label: "Jefferson", value: 2, component: JeffersonTab },
      { label: "Joint", value: 3, component: JointTab },
      { label: "House Projects", value: 4, component: HouseProjectsTab },
      { label: "Income", value: 5, component: IncomeTab },
    ];
  </script>
  
  <Tabs {items} />
  