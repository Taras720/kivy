from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.button import Button
from kivy.uix.floatlayout import FloatLayout
from kivy.uix.textinput import TextInput
from kivy.uix.screenmanager import ScreenManager, Screen
from kivy.uix.scrollview import ScrollView

class MainScreen(Screen):
    def __init__(self, **kwargs):
        super(MainScreen, self).__init__(**kwargs)
        layout = FloatLayout()

        label = Label(text="Вибери екран", size_hint=(1, 0.2), pos_hint={'center_x': 0.3, 'center_y': 0.5})
        btn1 = Button(text="Кнопка 1", size_hint=(0.5, 0.25), pos_hint={'center_x': 0.8, 'center_y': 0.9})
        btn2 = Button(text="Кнопка 2", size_hint=(0.5, 0.25), pos_hint={'center_x': 0.8, 'center_y': 0.65})
        btn3 = Button(text="Кнопка 3", size_hint=(0.5, 0.25), pos_hint={'center_x': 0.8, 'center_y': 0.4})
        btn4 = Button(text="Кнопка 4", size_hint=(0.5, 0.25), pos_hint={'center_x': 0.8, 'center_y': 0.15})

        layout.add_widget(label)
        layout.add_widget(btn1)
        layout.add_widget(btn2)
        layout.add_widget(btn3)
        layout.add_widget(btn4)

        self.add_widget(layout)

        btn1.bind(on_press=self.next_screen)
        btn2.bind(on_press=self.next_second)
        btn3.bind(on_press=self.next_third)
        btn4.bind(on_press=self.next_fourth)

    def next_screen(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'first'

    def next_second(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'second'
    
    def next_third(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'third'

    def next_fourth(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'fourth'

class FirstScreen(Screen):
    def __init__(self, **kwargs):
        super(FirstScreen, self).__init__(**kwargs)
        layout = FloatLayout()
        btn_1 = Button(text="Назад", size_hint=(0.3, 0.2), pos_hint={'center_x': 0.3, 'center_y': 0.6})
        btn_2 = Button(text="Вибір 1", size_hint=(0.3, 0.2), pos_hint={'center_x': 0.5, 'center_y': 0.4})

        layout.add_widget(btn_1)
        layout.add_widget(btn_2)

        self.add_widget(layout)

        btn_1.bind(on_press=self.back)
        btn_2.bind(on_press=self.next_screen)

    def back(self, instance):
        self.manager.transition.direction = 'right'
        self.manager.current = 'main'

    def next_screen(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'second'

class SecondScreen(Screen):
    def __init__(self, **kwargs):
        super(SecondScreen, self).__init__(**kwargs)
        layout = FloatLayout()
        self.text = TextInput(size_hint=(0.3, 0.05), pos_hint={'center_x': 0.53, 'center_y': 0.23})
        label4 = Label(text="Вибір 2", pos_hint={'center_x': 0.5, 'center_y': 0.6})
        label3 = Label(text="Введіть пароль ", pos_hint={'center_x': 0.3, 'center_y': 0.22})
        btn_1 = Button(text="Назад", size_hint=(0.2, 0.15), pos_hint={'center_x': 0.4, 'center_y': 0.1})
        btn_2 = Button(text="Ок", size_hint=(0.2, 0.15), pos_hint={'center_x': 0.6, 'center_y': 0.1})

        layout.add_widget(btn_1)
        layout.add_widget(btn_2)
        layout.add_widget(label4)
        layout.add_widget(label3)
        layout.add_widget(self.text)

        self.add_widget(layout)

        btn_1.bind(on_press=self.back)
        btn_2.bind(on_press=self.next_screen)

    def back(self, instance):
        self.manager.transition.direction = 'right'
        self.manager.current = 'main'

    def next_screen(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'third'

class ThirdScreen(Screen):
    def __init__(self, **kwargs):
        super(ThirdScreen, self).__init__(**kwargs)
        layout = FloatLayout()

        self.scroll_view = ScrollView(size_hint=(0.9, 0.6), pos_hint={'center_x': 0.5, 'center_y': 0.6})
        self.label = Label(size_hint_y=None, text="Третій екран", text_size=(self.width, None))
        self.label.bind(texture_size=self.update_height)
        self.scroll_view.add_widget(self.label)

        self.show_button = Button(text="Показати введені дані", size_hint=(0.5, 0.15), pos_hint={'center_x': 0.5, 'center_y': 0.5})
        self.back_button = Button(text="Назад", size_hint=(0.5, 0.15), pos_hint={'center_x': 0.5, 'center_y': 0.1})
        self.next_button = Button(text="Вибір 3", size_hint=(0.5, 0.15), pos_hint={'center_x': 0.5, 'center_y': 0.3})

        self.show_button.bind(on_press=self.show_data)
        self.back_button.bind(on_press=self.back)
        self.next_button.bind(on_press=self.next)

        layout.add_widget(self.scroll_view)
        layout.add_widget(self.show_button)
        layout.add_widget(self.back_button)
        layout.add_widget(self.next_button)
        
        self.add_widget(layout)

    def update_height(self, *args):
        self.label.height = self.label.texture_size[1]

    def show_data(self, instance):
        second_screen = self.manager.get_screen('second')
        self.label.text = f"Введені дані: {second_screen.text.text}"

    def back(self, instance):
        self.manager.transition.direction = 'right'
        self.manager.current = 'main'

    def next(self, instance):
        self.manager.transition.direction = 'left'
        self.manager.current = 'fourth'

class FourthScreen(Screen):
    def __init__(self, **kwargs):
        super(FourthScreen, self).__init__(**kwargs)
        layout = FloatLayout()

        # Довгий текст для демонстрації прокручування
        long_text = (
            "Це дуже довгий текст. " * 50 +
            "Він призначений для демонстрації функції прокручування. " * 50 +
            "Прокрутіть вниз, щоб побачити весь текст."
        )

        self.scroll_view = ScrollView(size_hint=(0.9, 0.6), pos_hint={'center_x': 0.5, 'center_y': 0.6})
        self.label = Label(size_hint_y=None, text=long_text, text_size=(self.width, None))
        self.label.bind(texture_size=self.update_height)
        self.scroll_view.add_widget(self.label)
        
        self.back_button = Button(text="Назад на головний екран", size_hint=(0.5, 0.15), pos_hint={'center_x': 0.5, 'center_y': 0.1})
        self.back_button.bind(on_press=self.back_to_main)

        layout.add_widget(self.scroll_view)
        layout.add_widget(self.back_button)

        self.add_widget(layout)

    def update_height(self, *args):
        self.label.height = self.label.texture_size[1]

    def back_to_main(self, instance):
        self.manager.transition.direction = 'right'
        self.manager.current = 'main'

class MyApp(App):
    def build(self):
        sm = ScreenManager()
        sm.add_widget(MainScreen(name='main'))
        sm.add_widget(FirstScreen(name='first'))
        sm.add_widget(SecondScreen(name='second'))
        sm.add_widget(ThirdScreen(name='third'))
        sm.add_widget(FourthScreen(name='fourth'))
        return sm

if __name__ == '__main__':
    MyApp().run()
