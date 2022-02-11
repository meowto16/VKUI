Компонент выбора даты.

**Обратите внимание:** Данный компонент предназначен для использования на desktop. При использовании на ios/android работа компонента не гарантируется

```jsx { "props": { "layout": false, "iframe": false } }
import { format } from "date-fns";

const Example = () => {
  const [value, setValue] = useState(new Date());
  const [enableTime, setEnableTime] = useState(false);
  const [disablePast, setDisablePast] = useState(false);
  const [disableFuture, setDisableFuture] = useState(false);
  const [locale, setLocale] = useState("ru");

  return (
    <View activePanel="calendar">
      <Panel id="calendar">
        <PanelHeader>DateInput</PanelHeader>
        <Group>
          <FormLayout>
            <FormLayoutGroup mode="vertical">
              <FormItem top="Выбор времени">
                <Checkbox
                  checked={enableTime}
                  onChange={(e) => setEnableTime(e.target.checked)}
                >
                  Включено
                </Checkbox>
              </FormItem>
              <FormItem top="Запрет выбора прошлых дат">
                <Checkbox
                  checked={disablePast}
                  onChange={(e) => setDisablePast(e.target.checked)}
                >
                  Включено
                </Checkbox>
              </FormItem>
              <FormItem top="Запрет выбора будущих дат">
                <Checkbox
                  checked={disableFuture}
                  onChange={(e) => setDisableFuture(e.target.checked)}
                >
                  Включено
                </Checkbox>
              </FormItem>
              <FormItem top="Локаль">
                <Select
                  style={{ width: 100 }}
                  value={locale}
                  onChange={(e) => setLocale(e.target.value)}
                  options={[
                    {
                      label: "ru",
                      value: "ru",
                    },
                    {
                      label: "en",
                      value: "en",
                    },
                    {
                      label: "ar",
                      value: "ar",
                    },
                    {
                      label: "fr",
                      value: "fr",
                    },
                  ]}
                />
              </FormItem>
              <FormItem>
                <div style={{ display: "flex" }}>
                  <DateInput
                    value={value}
                    onChange={setValue}
                    enableTime={enableTime}
                    disablePast={disablePast}
                    disableFuture={disableFuture}
                    locale={locale}
                  />
                </div>
              </FormItem>
            </FormLayoutGroup>
          </FormLayout>
        </Group>
      </Panel>
    </View>
  );
};

<Example />;
```