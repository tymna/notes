- contract *class* (code)
- contract *instance* (address) (holds pointer to a *class* and all storage)
- to upgrade means "change instance's pointer to which class it uses (instance has a class-id field)"
	same [[proxy and implementation]]
so i can register a new *class*, and point old *instance* to that new *class*

- immutability by default
- to add upgradeablility: add the upgrade hook
 #[external("private")]
fn update_to(new_class: ContractClassId) {
	self.enqueue(ContractInstanceRegistry::at(CONTRACT_INSTANCE_REGISTRY_CONTRACT_ADDRESS).update(new_class));
      }
class id -> compute from compiled artifact (from target) (just the hash of the code)
const classId = (await getContractClassFromArtifact(CounterV2Artifact)).id;
register class id on-chain:
await publishContractClass(wallet, CounterV2Artifact);
trigger the upgrade:
await counter.methods.update_to(classId).send({ from: account })


- update delay
- access control
- upgrade with no "update_to" -> contract becomes immutable (immutability locked)
- new class' initializer does not work, new storage starts with 0 (if needs to be populated we can use separate function after deployment)
- need to re-register the contract for PXE (wallet.registerContract) -> built-in in our app, so done automatically to user