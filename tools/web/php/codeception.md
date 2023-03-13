# acceptance

# unit
- classes:
```
use Tests\Support\UnitTester;
use Codeception\Verify\Verify;
use \Codeception\Stub\Expected;
```
- Verify
    - `verify($value)->equals($expected)`
    - `verify($value)->equalsIgnoringCase($expected)`
- Mocks:
```
$mock = $this->make(ClassName::class, [
        'func' => 'return',
        'func2' => Expected::once($function),
    ]);
```
- Expect:
    - `Expected::once($function)`: one execution of function
    - `Expected::exact(num, $function)`: num executions of function